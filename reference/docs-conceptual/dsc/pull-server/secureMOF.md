---
ms.date: 10/31/2017
keywords: dsc,powershell,configuration,setup
title: Proteger el archivo MOF
ms.openlocfilehash: 4ca540303cb740ac602bce181e0e446efcd16b6e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953562"
---
# <a name="securing-the-mof-file"></a>Proteger el archivo MOF

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC administra la configuración de nodos de servidor aplicando la información almacenada en un archivo MOF, donde el administrador de configuración local (LCM) implementa el estado final que quiere.
Como este archivo contiene los detalles de la configuración, es importante que esté protegido.
En este tema se describe cómo asegurarse de que el nodo de destino ha cifrado el archivo.

Desde PowerShell 5.0, el archivo MOF completo se cifra de forma predeterminada cuando se aplica al nodo por medio del cmdlet `Start-DSCConfiguration`.
El proceso descrito en este artículo únicamente es necesario si se implementa una solución a través del protocolo de servicio de incorporación de cambios cuando los certificados no se administran. De este modo, se garantiza que el sistema puede descifrar y leer las configuraciones descargadas por el nodo de destino antes de que se apliquen (por ejemplo, el servicio de incorporación de cambios disponible en Windows Server).
El servicio instalará y administrará automáticamente los certificados relativos a los nodos registrados en [DSC de Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-overview), sin que ello suponga ninguna sobrecarga administrativa.

> [!NOTE]
> En este tema se describen los certificados usados para el cifrado.
> Para el cifrado, un certificado autofirmado es suficiente, porque la clave privada se mantiene siempre secreta y el cifrado no implica la confianza del documento.
> Los certificados autofirmados *no* deben usarse con fines de autenticación.
> Debe usar un certificado de una entidad de certificación de confianza (CA) para fines de autenticación.

## <a name="prerequisites"></a>Requisitos previos

Para cifrar correctamente las credenciales utilizadas para proteger una configuración DSC, asegúrese de que disponer de lo siguiente:

- **Algún medio de emisión y distribución de certificados**. En este tema y en sus ejemplos se supone que usa la entidad de certificación de Active Directory. Para obtener información más en profundidad sobre los Servicios de certificados de Active Directory, vea [Información general de Servicios de certificados de Active Directory](https://technet.microsoft.com/library/hh831740.aspx) y [Servicios de certificados de Active Directory](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Acceso administrativo a los nodos de destino**.
- **Cada uno de los nodos de destino tiene un certificado de cifrado guardado en su almacén personal**. En Windows PowerShell, la ruta de acceso al almacén es Cert:\LocalMachine\My. En los ejemplos de este tema se usa la plantilla de "autenticación de estación de trabajo", que puede encontrar (junto con otras plantillas de certificado) en las [Plantillas de certificado predeterminadas](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Si va a ejecutar esta configuración en un equipo distinto al nodo de destino, **exporte la clave pública del certificado** y luego impórtela en el equipo desde el que se va a ejecutar la configuración. Asegúrese de que solo se exporte la clave **public**; mantenga la clave privada segura.

## <a name="overall-process"></a>Proceso general

 1. Configure los certificados, las claves y las huellas digitales, asegurándose de que cada nodo de destino tenga copias del certificado y de que el equipo de configuración tenga la huella digital y la clave pública.
 2. Cree un bloque de datos de configuración que contenga la ruta de acceso y la huella digital de la clave pública.
 3. Cree un script de configuración que defina la configuración deseada para el nodo de destino y configure el descifrado en los nodos de destino, estableciendo que el administrador de configuración local descifre los datos de configuración con el certificado y su huella digital.
 4. Ejecute la configuración, que establecerá la configuración del administrador de configuración local e inicie la configuración DSC.

![Diagrama1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Requisitos de certificados

Para representar el cifrado de credenciales, se requiere que un certificado de clave pública esté disponible en el _nodo de destino_ en el que **confíe** el equipo usado para crear la configuración de DSC.
Este certificado de clave pública tiene requisitos específicos que debe usar para el cifrado de credenciales de DSC:

1. **Uso de la clave**:
   - Debe contener: "KeyEncipherment" y "DataEncipherment".
   - _No_ debe contener: "Digital Signature".
2. **Uso mejorado de clave**:
   - Debe contener: Cifrado del documento (1.3.6.1.4.1.311.80.1).
   - _No_ debe contener: Autenticación de cliente (1.3.6.1.5.5.7.3.2) y autenticación de servidor (1.3.6.1.5.5.7.3.1).
3. La clave privada del certificado está disponible en \*el nodo de destino.
4. El **proveedor** del certificado debe ser "Proveedor de servicios criptográficos de Microsoft RSA SChannel".

> [!IMPORTANT]
> Aunque puede usar un certificado que contenga un uso de clave de "Firma digital" o uno de los EKU de autenticación, esto permitirá que la clave de cifrado se use más fácilmente de forma inadecuada y sea vulnerable a ataques. Por lo tanto, le recomendamos que utilice un certificado creado específicamente con el fin de proteger las credenciales de DSC que omita estos EKU y usos de clave.

Cualquier certificado existente en el _nodo de destino_ que cumpla estos criterios puede usarse para proteger las credenciales de DSC.

## <a name="certificate-creation"></a>Creación de certificados

Existen dos enfoques que puede realizar para crear y usar el certificado de cifrado necesario (par de claves pública y privada).

1. Creación en el **nodo de destino** y exportación de únicamente la clave pública al **nodo de creación**
2. Creación en el **nodo de creación** y exportación del par de claves completo al **nodo de destino**

Se recomienda el método 1 porque la clave privada que se usa para descifrar las credenciales en el MOF permanece en el nodo de destino en todo momento.

### <a name="creating-the-certificate-on-the-target-node"></a>Creación del certificado en el nodo de destino

La clave privada debe mantenerse secreta, ya que se usa para descifrar el MOF en el **nodo de destino**. La forma más sencilla de hacerlo es crear el certificado de clave privada en el **nodo de destino** y copiar el **certificado de clave pública** en el equipo que se usa para crear la configuración de DSC en un archivo MOF.
En el ejemplo siguiente:

1. crea un certificado en el **nodo de destino**.
2. exporta el certificado de clave pública al **nodo de destino**.
3. importa el certificado de clave pública en **mi** almacén de certificados en el **nodo de creación**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>En el nodo de destino: creación y exportación de certificados

> Nodo de destino: Windows Server 2016 y Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Una vez exportado, el `DscPublicKey.cer` tendría que copiarse en el **nodo de creación**.

> Nodo de destino: Windows Server 2012 R2/Windows 8.1 y anteriores
> [!WARNING]
> Dado que el cmdlet `New-SelfSignedCertificate` en sistemas operativos anteriores a Windows 10 y Windows Server 2016 no admite el parámetro **Type**, en estos sistemas operativos es necesario un método alternativo para crear este certificado.
>
> En este caso puede usar `makecert.exe` o `certutil.exe` para crear el certificado.
>
>Un método alternativo consiste en [descargar el script New-SelfSignedCertificateEx.ps1 desde el centro de scripts de Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) y usarlo para crear el certificado:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Una vez exportado, el ```DscPublicKey.cer``` tendría que copiarse en el **nodo de creación**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>En el nodo de creación: importación de la clave pública del certificado

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Creación del certificado en el nodo de creación

Como alternativa, se puede crear el certificado de cifrado en el **nodo de creación**, exportarlo con la **clave privada** como archivo PFX y después importarlo en el **nodo de destino**.
Este es el método actual para implementar el cifrado de credenciales de DSC en _Nano Server_.
Aunque el PFX está protegido con una contraseña, debe estar protegido durante el tránsito.
En el ejemplo siguiente:

1. crea un certificado en el **nodo de creación**.
2. exporta el certificado, incluida la clave privada, en el **nodo de creación**.
3. quita la clave privada del **nodo de creación**, pero mantiene el certificado de clave pública de **mi** almacén.
4. importa el certificado de clave privada al almacén de certificados My(Personal) en el **nodo de destino**.
   - debe agregarse al almacén raíz, de forma que este será de confianza para el **nodo de destino**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>En el nodo de creación: creación y exportación de certificados

> Nodo de destino: Windows Server 2016 y Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

Una vez exportado, el `DscPrivateKey.pfx` tendría que copiarse en el **nodo de destino**.

> Nodo de destino: Windows Server 2012 R2/Windows 8.1 y anteriores
> [!WARNING]
> Dado que el cmdlet `New-SelfSignedCertificate` en sistemas operativos anteriores a Windows 10 y Windows Server 2016 no admite el parámetro **Type**, en estos sistemas operativos es necesario un método alternativo para crear este certificado.
>
> En este caso puede usar `makecert.exe` o `certutil.exe` para crear el certificado.
>
> Un método alternativo consiste en [descargar el script New-SelfSignedCertificateEx.ps1 desde el centro de scripts de Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) y usarlo para crear el certificado:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>En el nodo de destino: importación de la clave privada del certificado raíz de confianza

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Datos de configuración

El bloque de datos de configuración define los nodos de destino en los que operará, si se cifrarán las credenciales o no, los medios de cifrado y otra información. Para más información sobre el bloque de datos de configuración, consulte [Separación de los datos de entorno y configuración](../configurations/configData.md).

Los elementos que se pueden configurar para cada nodo que están relacionados con el cifrado de credenciales son:

- **NodeName**: nombre del nodo de destino para el que se configura el cifrado de credenciales.
- **PsDscAllowPlainTextPassword**: indica si las credenciales sin cifrar se pueden pasar a este nodo. Esto **no se recomienda**.
- **Huella digital**: huella digital del certificado que se usará para descifrar las credenciales en la configuración de DSC en el _nodo de destino_. **Este certificado debe existir en el almacén de certificados de la máquina local en el nodo de destino.**
- **CertificateFile**: archivo de certificado (que solo contiene la clave pública) que debe usarse para cifrar las credenciales para el _nodo de destino_. Debe ser un archivo de certificados con formato X.509 codificado base 64 o DER binario codificado X.509.

En este ejemplo se muestra un bloque de datos de configuración que especifica un nodo de destino en el que se actuará con el nombre targetNode, la ruta de acceso al archivo de certificado de clave pública (denominado targetNode.cer) y la huella digital de la clave pública.

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a>Script de configuración

En el script de configuración, utilice el parámetro `PsCredential` para garantizar que las credenciales se almacenen durante el menor tiempo posible. Al ejecutar el ejemplo facilitado, DSC pedirá las credenciales y luego cifrará el archivo MOF con el elemento CertificateFile que esté asociado con el nodo de destino en el bloque de datos de configuración. Este ejemplo de código copia un archivo desde un recurso compartido que está protegido para un usuario.

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a>Configuración del descifrado

Antes de que [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) pueda funcionar, debe indicar al administrador de configuración local en cada nodo de destino qué certificado se usará para descifrar las credenciales, mediante el recurso CertificateID para comprobar la huella digital del certificado. Esta función de ejemplo encontrará el certificado local adecuado (es posible que deba personalizarlo para que encuentre el certificado exacto que quiere utilizar):

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

Con el certificado identificado mediante su huella digital, el script de configuración se puede actualizar para utilizar el valor:

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a>Ejecución de la configuración

En este punto, puede ejecutar la configuración, lo que dará como resultado dos archivos:

- Un archivo *.meta.mof que configura el administrador de configuración local para que descifre las credenciales mediante el certificado que está almacenado en el almacén de la máquina local y se identifique mediante su huella digital. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) se aplica al archivo *.meta.mof.
- Un archivo MOF que aplica realmente la configuración. Start-DscConfiguration aplica la configuración.

Estos comandos llevará a cabo esos pasos:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

En este ejemplo se insertaría la configuración de DSC en el nodo de destino.
La configuración de DSC también se puede aplicar mediante un servidor de incorporación de cambios de DSC, si está disponible.

Consulte [Setting up a DSC pull client](pullClient.md) (Configuración de un cliente de extracción de DSC) para obtener más información sobre cómo aplicar configuraciones de DSC mediante un servidor de incorporación de cambios de DSC.

## <a name="credential-encryption-module-example"></a>Ejemplo de módulo de cifrado de credenciales

Este es un ejemplo completo que incorpora todos estos pasos, además de un cmdlet del asistente que exporta y copia las claves públicas:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
