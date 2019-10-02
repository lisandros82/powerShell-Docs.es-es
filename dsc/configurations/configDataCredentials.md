---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Opciones de credenciales en los datos de configuración
ms.openlocfilehash: 660c3643f7eb2e9ccb91bd992747fb9d5da0ccdb
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323297"
---
# <a name="credentials-options-in-configuration-data"></a>Opciones de credenciales en los datos de configuración

>Se aplica a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Contraseñas de texto sin formato y usuarios del dominio

Las configuraciones DSC que contienen una credencial sin cifrado generarán un mensaje de error sobre contraseñas de texto sin formato.
Además, DSC generará una advertencia cuando se usen credenciales de dominio.
Para suprimir estos mensajes de advertencia y de error, utilice las palabras clave de datos de configuración DSC:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> En general, no es seguro almacenar o transmitir contraseñas de texto sin formato y no cifradas. Se recomienda proteger las credenciales mediante el uso de las técnicas que se describirán más adelante en este tema.
> El servicio DSC de Azure Automation le permite administrar de forma centralizada las credenciales que se deben compilar en las configuraciones y almacenar de forma segura.
> Para obtener información, consulte: [Compilación de configuraciones DSC y Recursos de credenciales](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Control de credenciales en DSC

Los recursos de configuración DSC se ejecutan como `Local System` de forma predeterminada.
Sin embargo, algunos recursos necesitan una credencial, por ejemplo cuando el recurso `Package` necesita instalar software en una cuenta de usuario concreta.

Los recursos anteriores utilizaban un nombre de propiedad `Credential` codificado de forma rígida para controlar esto.
WMF 5.0 agregó una propiedad `PsDscRunAsCredential` automática para todos los recursos.
Para obtener más información sobre cómo usar `PsDscRunAsCredential`, vea [DSC de ejecución con las credenciales de usuario](runAsUser.md).
Los recursos más recientes y los recursos personalizados pueden utilizar esta propiedad automática en lugar de crear su propia propiedad para las credenciales.

> [!NOTE]
> El diseño de algunos recursos implica que se van a usar varias credenciales para un motivo concreto y tendrán sus propias propiedades de credencial.

Para encontrar las propiedades de credenciales disponibles en un recurso, use `Get-DscResource -Name ResourceName -Syntax` o Intellisense en el ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

En este ejemplo se utiliza un recurso [Group](../resources/resources.md) del módulo de recursos integrado de DSC `PSDesiredStateConfiguration`.
Puede crear grupos locales y agregar o quitar miembros.
Acepta tanto la propiedad `Credential` como la propiedad automática `PsDscRunAsCredential`.
No obstante, el recurso solo utiliza la propiedad `Credential`.

Para más información sobre la propiedad `PsDscRunAsCredential`, consulte [DSC de ejecución con las credenciales de usuario](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Ejemplo: la propiedad Credential del recurso Group

DSC se ejecuta en `Local System`, por lo que ya tiene permisos para cambiar grupos y usuarios locales.
Si el miembro agregado es una cuenta local, no se necesitan credenciales.
Si el recurso `Group` agrega una cuenta de dominio al grupo local, es necesaria una credencial.

No se permiten las consultas anónimas a Active Directory.
La propiedad `Credential` del recurso `Group` es la cuenta de dominio que se utiliza para consultar a Active Directory.
En la mayoría de casos esto podría deberse a una cuenta de usuario genérica ya que, de forma predeterminada, los usuarios pueden *leer* la mayoría de objetos de Active Directory.

## <a name="example-configuration"></a>Configuración de ejemplo

En el ejemplo de código siguiente se utiliza DSC para rellenar un grupo local con un usuario de dominio:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Este código genera un error y un mensaje de advertencia:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Este ejemplo tiene dos problemas:

1. Un error explica que no se recomiendan las contraseñas de texto sin formato.
2. Una advertencia recomienda que no se use una credencial de dominio.

Las marcas de **PSDSCAllowPlainTextPassword** y **PSDSCAllowDomainUser** suprimen el error y la advertencia que informan al usuario del riesgo que conlleva.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

El primer mensaje de error tiene una dirección URL con documentación.
En este vínculo se explica cómo cifrar contraseñas con una estructura [ConfigurationData](./configData.md) y un certificado.
Para más información sobre certificados y DSC, [lea esta publicación](https://aka.ms/certs4dsc).

Para forzar una contraseña de texto sin formato, el recurso requiere la palabra clave `PsDscAllowPlainTextPassword` en la sección de datos de configuración, como se indica a continuación:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

La marca **PSDSCAllowPlainTextPassword** requiere que el usuario reconozca el riesgo de almacenar contraseñas de texto sin formato en un archivo MOF. En el archivo MOF generado, aunque se utilizó un objeto **PSCredential** que contenía un valor **SecureString**, las contraseñas aún aparecen como texto sin formato. Esta es la única vez que se exponen las credenciales. Al obtener acceso a este archivo MOF, cualquier persona puede acceder a la cuenta de administrador.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Credenciales en tránsito y en reposo

- La marca **PSDscAllowPlainTextPassword** permite la compilación de archivos MOF que contienen contraseñas como texto no cifrado.
  Tome precauciones cuando almacene archivos MOF que contienen contraseñas de texto no cifrado.
- Cuando el archivo MOF se entrega a un nodo en modo de **inserción**, WinRM cifra la comunicación para proteger la contraseña de texto no cifrado a menos que reemplace el valor predeterminado por el parámetro **AllowUnencrypted**.
  - El cifrado del MOF con un certificado protege el archivo MOF en reposo antes de que se haya aplicado a un nodo.
- En el modo de **extracción**, puede configurar el servidor de extracción de Windows para usar HTTPS para el cifrado del tráfico mediante el protocolo especificado en Internet Information Server. Para obtener más información, consulte los artículos [Configuración de un cliente de extracción de DSC](../pull-server/pullclient.md) y [Proteger el archivo MOF](../pull-server/secureMOF.md).
  - En el servicio [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview), siempre se cifra el tráfico de extracción.
- En el nodo, los archivos MOF se cifran en reposo a partir de PowerShell 5.0.
  - En PowerShell 4.0, los archivos MOF no se cifran en reposo, a menos que se cifrasen con un certificado cuando se insertaron en el nodo o se extrajeron de él.

**Microsoft aconseja evitar las contraseñas de texto sin formato por sus riesgos de seguridad considerables.**

## <a name="domain-credentials"></a>Credenciales de dominio

Si se ejecuta de nuevo el script de configuración de ejemplo (con o sin cifrado), se sigue generando la advertencia que indica que no se recomienda el uso de una cuenta de dominio para una credencial.
Si se utiliza una cuenta local, se elimina la posible exposición de credenciales de dominio podría usarse en otros servidores.

**Cuando se usan credenciales con recursos de DSC, siempre que sea posible es preferible usar una cuenta local en lugar de una cuenta de dominio.**

Si hay un carácter '\\' o '\@' en la propiedad `Username` de la credencial, DSC lo tratará como una cuenta de dominio.
Existen excepciones para "localhost", "127.0.0.1" y "::1" en la parte del dominio del nombre de usuario.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

En el ejemplo del recurso `Group` de DSC anterior, la consulta a un dominio de Active Directory *requiere* una cuenta de dominio.
En este caso, agregue la propiedad `PSDscAllowDomainUser` al bloque `ConfigurationData` como se indica a continuación:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Ahora, el script de configuración generará el archivo MOF sin errores ni advertencias.
