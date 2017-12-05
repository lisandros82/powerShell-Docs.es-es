---
ms.date: 2017-10-31
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Proteger el archivo MOF
ms.openlocfilehash: ed9d259e2cd963560ad6f5b60702c54e2fa36900
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2017
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="aee11-103">Proteger el archivo MOF</span><span class="sxs-lookup"><span data-stu-id="aee11-103">Securing the MOF File</span></span>

><span data-ttu-id="aee11-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aee11-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aee11-105">DSC administra la configuración de nodos de servidor aplicando la información almacenada en un archivo MOF, donde el administrador de configuración local (LCM) implementa el estado final que quiere.</span><span class="sxs-lookup"><span data-stu-id="aee11-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="aee11-106">Como este archivo contiene los detalles de la configuración, es importante que esté protegido.</span><span class="sxs-lookup"><span data-stu-id="aee11-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="aee11-107">En este tema se describe cómo asegurarse de que el nodo de destino ha cifrado el archivo.</span><span class="sxs-lookup"><span data-stu-id="aee11-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="aee11-108">Desde PowerShell 5.0, el archivo MOF completo se cifra de forma predeterminada cuando se aplica al nodo por medio del cmdlet **Start-DSCConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="aee11-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the **Start-DSCConfiguration** cmdlet.</span></span>
<span data-ttu-id="aee11-109">El proceso descrito en este artículo únicamente es necesario si se implementa una solución a través del protocolo de servicio de incorporación de cambios cuando los certificados no se administran. De este modo, se garantiza que el sistema puede descifrar y leer las configuraciones descargadas por el nodo de destino antes de que se apliquen (por ejemplo, el servicio de incorporación de cambios disponible en Windows Server).</span><span class="sxs-lookup"><span data-stu-id="aee11-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="aee11-110">El servicio instalará y administrará automáticamente los certificados relativos a los nodos registrados en [DSC de Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview), sin que ello suponga ninguna sobrecarga administrativa.</span><span class="sxs-lookup"><span data-stu-id="aee11-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

><span data-ttu-id="aee11-111">**Nota:** En este tema se describen los certificados usados para el cifrado.</span><span class="sxs-lookup"><span data-stu-id="aee11-111">**Note:** This topic discusses certificates used for encryption.</span></span>
><span data-ttu-id="aee11-112">Para el cifrado, un certificado autofirmado es suficiente, porque la clave privada se mantiene siempre secreta y el cifrado no implica la confianza del documento.</span><span class="sxs-lookup"><span data-stu-id="aee11-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
><span data-ttu-id="aee11-113">Los certificados autofirmados *no* deben usarse con fines de autenticación.</span><span class="sxs-lookup"><span data-stu-id="aee11-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
><span data-ttu-id="aee11-114">Debe usar un certificado de una entidad de certificación de confianza (CA) para fines de autenticación.</span><span class="sxs-lookup"><span data-stu-id="aee11-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aee11-115">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="aee11-115">Prerequisites</span></span>

<span data-ttu-id="aee11-116">Para cifrar correctamente las credenciales utilizadas para proteger una configuración DSC, asegúrese de que disponer de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="aee11-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="aee11-117">**Algún medio de emisión y distribución de certificados**.</span><span class="sxs-lookup"><span data-stu-id="aee11-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="aee11-118">En este tema y en sus ejemplos se supone que usa la entidad de certificación de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="aee11-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="aee11-119">Para obtener información más en profundidad sobre los Servicios de certificados de Active Directory, vea [Información general de Servicios de certificados de Active Directory](https://technet.microsoft.com/library/hh831740.aspx) y [Servicios de certificados de Active Directory](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="aee11-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="aee11-120">**Acceso administrativo a los nodos de destino**.</span><span class="sxs-lookup"><span data-stu-id="aee11-120">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="aee11-121">**Cada uno de los nodos de destino tiene un certificado de cifrado guardado en su almacén personal**.</span><span class="sxs-lookup"><span data-stu-id="aee11-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="aee11-122">En Windows PowerShell, la ruta de acceso al almacén es Cert:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="aee11-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="aee11-123">En los ejemplos de este tema se usa la plantilla de "autenticación de estación de trabajo", que puede encontrar (junto con otras plantillas de certificado) en las [Plantillas de certificado predeterminadas](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="aee11-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="aee11-124">Si va a ejecutar esta configuración en un equipo distinto al nodo de destino, **exporte la clave pública del certificado** y luego impórtela en el equipo desde el que se va a ejecutar la configuración.</span><span class="sxs-lookup"><span data-stu-id="aee11-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="aee11-125">Asegúrese de que solo se exporte la clave **public**; mantenga la clave privada segura.</span><span class="sxs-lookup"><span data-stu-id="aee11-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="aee11-126">Proceso general</span><span class="sxs-lookup"><span data-stu-id="aee11-126">Overall process</span></span>

 1. <span data-ttu-id="aee11-127">Configure los certificados, las claves y las huellas digitales, asegurándose de que cada nodo de destino tenga copias del certificado y de que el equipo de configuración tenga la huella digital y la clave pública.</span><span class="sxs-lookup"><span data-stu-id="aee11-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="aee11-128">Cree un bloque de datos de configuración que contenga la ruta de acceso y la huella digital de la clave pública.</span><span class="sxs-lookup"><span data-stu-id="aee11-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="aee11-129">Cree un script de configuración que defina la configuración deseada para el nodo de destino y configure el descifrado en los nodos de destino, estableciendo que el administrador de configuración local descifre los datos de configuración con el certificado y su huella digital.</span><span class="sxs-lookup"><span data-stu-id="aee11-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="aee11-130">Ejecute la configuración, que establecerá la configuración del administrador de configuración local e inicie la configuración DSC.</span><span class="sxs-lookup"><span data-stu-id="aee11-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagrama1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="aee11-132">Requisitos de certificados</span><span class="sxs-lookup"><span data-stu-id="aee11-132">Certificate Requirements</span></span>

<span data-ttu-id="aee11-133">Para representar el cifrado de credenciales, se requiere que un certificado de clave pública esté disponible en el _nodo de destino_ en el que **confíe** el equipo usado para crear la configuración de DSC.</span><span class="sxs-lookup"><span data-stu-id="aee11-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="aee11-134">Este certificado de clave pública tiene requisitos específicos que debe usar para el cifrado de credenciales de DSC:</span><span class="sxs-lookup"><span data-stu-id="aee11-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="aee11-135">**Uso de la clave**:</span><span class="sxs-lookup"><span data-stu-id="aee11-135">**Key Usage**:</span></span>
   - <span data-ttu-id="aee11-136">Debe contener: 'KeyEncipherment' y 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="aee11-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="aee11-137">_No_ debe contener: 'Digital Signature'.</span><span class="sxs-lookup"><span data-stu-id="aee11-137">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="aee11-138">**Uso mejorado de clave**:</span><span class="sxs-lookup"><span data-stu-id="aee11-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="aee11-139">Debe contener: cifrado del documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="aee11-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="aee11-140">_No_ debe contener: autenticación de cliente (1.3.6.1.5.5.7.3.2) ni autenticación de servidor (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="aee11-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="aee11-141">La clave privada del certificado está disponible en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="aee11-141">The Private Key for the certificate is available on the *Target Node_.</span></span>
 4. <span data-ttu-id="aee11-142">El **proveedor** del certificado debe ser "Proveedor de servicios criptográficos de Microsoft RSA SChannel".</span><span class="sxs-lookup"><span data-stu-id="aee11-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>
 
><span data-ttu-id="aee11-143">**Procedimiento recomendado:** aunque puede usar un certificado que contenga un uso de clave de "Firma digital" o uno de los EKU de autenticación, esto permitirá que la clave de cifrado se use más fácilmente de forma inadecuada y sea vulnerable a ataques.</span><span class="sxs-lookup"><span data-stu-id="aee11-143">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="aee11-144">Por lo tanto, le recomendamos que utilice un certificado creado específicamente con el fin de proteger las credenciales de DSC que omita estos EKU y usos de clave.</span><span class="sxs-lookup"><span data-stu-id="aee11-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>
  
<span data-ttu-id="aee11-145">Cualquier certificado existente en el _nodo de destino_ que cumpla estos criterios puede usarse para proteger las credenciales de DSC.</span><span class="sxs-lookup"><span data-stu-id="aee11-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="aee11-146">Creación de certificados</span><span class="sxs-lookup"><span data-stu-id="aee11-146">Certificate creation</span></span>

<span data-ttu-id="aee11-147">Existen dos enfoques que puede realizar para crear y usar el certificado de cifrado necesario (par de claves pública y privada).</span><span class="sxs-lookup"><span data-stu-id="aee11-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="aee11-148">Creación en el **nodo de destino** y exportación de únicamente la clave pública al **nodo de creación**</span><span class="sxs-lookup"><span data-stu-id="aee11-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="aee11-149">Creación en el **nodo de creación** y exportación del par de claves completo al **nodo de destino**</span><span class="sxs-lookup"><span data-stu-id="aee11-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="aee11-150">Se recomienda el método 1 porque la clave privada que se usa para descifrar las credenciales en el MOF permanece en el nodo de destino en todo momento.</span><span class="sxs-lookup"><span data-stu-id="aee11-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="aee11-151">Creación del certificado en el nodo de destino</span><span class="sxs-lookup"><span data-stu-id="aee11-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="aee11-152">La clave privada debe mantenerse secreta, ya que se usa para descifrar el MOF en el **nodo de destino**. La forma más sencilla de hacerlo es crear el certificado de clave privada en el **nodo de destino** y copiar el **certificado de clave pública** en el equipo que se usa para crear la configuración de DSC en un archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="aee11-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="aee11-153">En el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="aee11-153">The following example:</span></span>
 1. <span data-ttu-id="aee11-154">crea un certificado en el **nodo de destino**.</span><span class="sxs-lookup"><span data-stu-id="aee11-154">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="aee11-155">exporta el certificado de clave pública al **nodo de destino**.</span><span class="sxs-lookup"><span data-stu-id="aee11-155">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="aee11-156">importa el certificado de clave pública en **mi** almacén de certificados en el **nodo de creación**.</span><span class="sxs-lookup"><span data-stu-id="aee11-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="aee11-157">En el nodo de destino: creación y exportación de certificados</span><span class="sxs-lookup"><span data-stu-id="aee11-157">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="aee11-158">Nodo de creación: Windows Server 2016 y Windows 10</span><span class="sxs-lookup"><span data-stu-id="aee11-158">Authoring Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="aee11-159">Una vez exportado, el ```DscPublicKey.cer``` tendría que copiarse en el **nodo de creación**.</span><span class="sxs-lookup"><span data-stu-id="aee11-159">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="aee11-160">Nodo de creación: Windows Server 2012 R2/Windows 8.1 y versiones anteriores</span><span class="sxs-lookup"><span data-stu-id="aee11-160">Authoring Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="aee11-161">Dado que el cmdlet New-SelfSignedCertificate en sistemas operativos anteriores a Windows 10 y Windows Server 2016 no admite el parámetro **Type**, en estos sistemas operativos es necesario un método alternativo para crear este certificado.</span><span class="sxs-lookup"><span data-stu-id="aee11-161">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="aee11-162">En este caso puede usar ```makecert.exe``` o ```certutil.exe``` para crear el certificado.</span><span class="sxs-lookup"><span data-stu-id="aee11-162">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="aee11-163">Un método alternativo consiste en [descargar el script New-SelfSignedCertificateEx.ps1 desde el centro de scripts de Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) y usarlo para crear el certificado:</span><span class="sxs-lookup"><span data-stu-id="aee11-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
    -StoreName 'My' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="aee11-164">Una vez exportado, el ```DscPublicKey.cer``` tendría que copiarse en el **nodo de creación**.</span><span class="sxs-lookup"><span data-stu-id="aee11-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="aee11-165">En el nodo de creación: importación de la clave pública del certificado</span><span class="sxs-lookup"><span data-stu-id="aee11-165">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="aee11-166">Creación del certificado en el nodo de creación</span><span class="sxs-lookup"><span data-stu-id="aee11-166">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="aee11-167">Como alternativa, se puede crear el certificado de cifrado en el **nodo de creación**, exportarlo con la **clave privada** como archivo PFX y después importarlo en el **nodo de destino**.</span><span class="sxs-lookup"><span data-stu-id="aee11-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="aee11-168">Este es el método actual para implementar el cifrado de credenciales de DSC en _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="aee11-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="aee11-169">Aunque el PFX está protegido con una contraseña, debe estar protegido durante el tránsito.</span><span class="sxs-lookup"><span data-stu-id="aee11-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="aee11-170">En el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="aee11-170">The following example:</span></span>
 1. <span data-ttu-id="aee11-171">crea un certificado en el **nodo de creación**.</span><span class="sxs-lookup"><span data-stu-id="aee11-171">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="aee11-172">exporta el certificado, incluida la clave privada, en el **nodo de creación**.</span><span class="sxs-lookup"><span data-stu-id="aee11-172">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="aee11-173">quita la clave privada del **nodo de creación**, pero mantiene el certificado de clave pública de **mi** almacén.</span><span class="sxs-lookup"><span data-stu-id="aee11-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="aee11-174">importa el certificado de clave privada en el almacén de certificados raíz en el **nodo de creación**.</span><span class="sxs-lookup"><span data-stu-id="aee11-174">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="aee11-175">debe agregarse al almacén raíz, de forma que este será de confianza para el **nodo de destino**.</span><span class="sxs-lookup"><span data-stu-id="aee11-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="aee11-176">En el nodo de creación: creación y exportación de certificados</span><span class="sxs-lookup"><span data-stu-id="aee11-176">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="aee11-177">Nodo de destino: Windows Server 2016 y Windows 10</span><span class="sxs-lookup"><span data-stu-id="aee11-177">Target Node: Windows Server 2016 and Windows 10</span></span>

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
<span data-ttu-id="aee11-178">Una vez exportado, el ```DscPrivateKey.pfx``` tendría que copiarse en el **nodo de destino**.</span><span class="sxs-lookup"><span data-stu-id="aee11-178">Once exported, the ```DscPrivateKey.pfx``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="aee11-179">Nodo de destino: Windows Server 2012 R2/Windows 8.1 y versiones anteriores</span><span class="sxs-lookup"><span data-stu-id="aee11-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="aee11-180">Dado que el cmdlet New-SelfSignedCertificate en sistemas operativos anteriores a Windows 10 y Windows Server 2016 no admite el parámetro **Type**, en estos sistemas operativos es necesario un método alternativo para crear este certificado.</span><span class="sxs-lookup"><span data-stu-id="aee11-180">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="aee11-181">En este caso puede usar ```makecert.exe``` o ```certutil.exe``` para crear el certificado.</span><span class="sxs-lookup"><span data-stu-id="aee11-181">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="aee11-182">Un método alternativo consiste en [descargar el script New-SelfSignedCertificateEx.ps1 desde el centro de scripts de Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) y usarlo para crear el certificado:</span><span class="sxs-lookup"><span data-stu-id="aee11-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="aee11-183">En el nodo de destino: importación de la clave privada del certificado raíz de confianza</span><span class="sxs-lookup"><span data-stu-id="aee11-183">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="aee11-184">Datos de configuración</span><span class="sxs-lookup"><span data-stu-id="aee11-184">Configuration data</span></span>

<span data-ttu-id="aee11-185">El bloque de datos de configuración define los nodos de destino en los que operará, si se cifrarán las credenciales o no, los medios de cifrado y otra información.</span><span class="sxs-lookup"><span data-stu-id="aee11-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="aee11-186">Para más información sobre el bloque de datos de configuración, consulte [Separación de los datos de entorno y configuración](configData.md).</span><span class="sxs-lookup"><span data-stu-id="aee11-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="aee11-187">Los elementos que se pueden configurar para cada nodo que están relacionados con el cifrado de credenciales son:</span><span class="sxs-lookup"><span data-stu-id="aee11-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="aee11-188">**NodeName**: nombre del nodo de destino para el que se configura el cifrado de credenciales.</span><span class="sxs-lookup"><span data-stu-id="aee11-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="aee11-189">**PsDscAllowPlainTextPassword**: indica si las credenciales sin cifrar se pueden pasar a este nodo.</span><span class="sxs-lookup"><span data-stu-id="aee11-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="aee11-190">Esto **no se recomienda**.</span><span class="sxs-lookup"><span data-stu-id="aee11-190">This is **not recommended**.</span></span>
* <span data-ttu-id="aee11-191">**Huella digital**: huella digital del certificado que se usará para descifrar las credenciales en la configuración de DSC en el _nodo de destino_.</span><span class="sxs-lookup"><span data-stu-id="aee11-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="aee11-192">**Este certificado debe existir en el almacén de certificados de la máquina local en el nodo de destino.**</span><span class="sxs-lookup"><span data-stu-id="aee11-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="aee11-193">**CertificateFile**: archivo de certificado (que solo contiene la clave pública) que debe usarse para cifrar las credenciales para el _nodo de destino_.</span><span class="sxs-lookup"><span data-stu-id="aee11-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="aee11-194">Debe ser un archivo de certificados con formato X.509 codificado base 64 o DER binario codificado X.509.</span><span class="sxs-lookup"><span data-stu-id="aee11-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="aee11-195">En este ejemplo se muestra un bloque de datos de configuración que especifica un nodo de destino en el que se actuará con el nombre targetNode, la ruta de acceso al archivo de certificado de clave pública (denominado targetNode.cer) y la huella digital de la clave pública.</span><span class="sxs-lookup"><span data-stu-id="aee11-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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


## <a name="configuration-script"></a><span data-ttu-id="aee11-196">Script de configuración</span><span class="sxs-lookup"><span data-stu-id="aee11-196">Configuration script</span></span>

<span data-ttu-id="aee11-197">En el script de configuración, utilice el parámetro `PsCredential` para garantizar que las credenciales se almacenen durante el menor tiempo posible.</span><span class="sxs-lookup"><span data-stu-id="aee11-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="aee11-198">Al ejecutar el ejemplo facilitado, DSC pedirá las credenciales y luego cifrará el archivo MOF con el elemento CertificateFile que esté asociado con el nodo de destino en el bloque de datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="aee11-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="aee11-199">Este ejemplo de código copia un archivo desde un recurso compartido que está protegido para un usuario.</span><span class="sxs-lookup"><span data-stu-id="aee11-199">This code example copies a file from a share that is secured to a user.</span></span>

```
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

## <a name="setting-up-decryption"></a><span data-ttu-id="aee11-200">Configuración del descifrado</span><span class="sxs-lookup"><span data-stu-id="aee11-200">Setting up decryption</span></span>

<span data-ttu-id="aee11-201">Antes de que [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) pueda funcionar, debe indicar al administrador de configuración local en cada nodo de destino qué certificado se usará para descifrar las credenciales, mediante el recurso CertificateID para comprobar la huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="aee11-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="aee11-202">Esta función de ejemplo encontrará el certificado local adecuado (es posible que deba personalizarlo para que encuentre el certificado exacto que quiere utilizar):</span><span class="sxs-lookup"><span data-stu-id="aee11-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="aee11-203">Con el certificado identificado mediante su huella digital, el script de configuración se puede actualizar para utilizar el valor:</span><span class="sxs-lookup"><span data-stu-id="aee11-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="aee11-204">Ejecución de la configuración</span><span class="sxs-lookup"><span data-stu-id="aee11-204">Running the configuration</span></span>

<span data-ttu-id="aee11-205">En este punto, puede ejecutar la configuración, lo que dará como resultado dos archivos:</span><span class="sxs-lookup"><span data-stu-id="aee11-205">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="aee11-206">Un archivo *.meta.mof que configura el administrador de configuración local para que descifre las credenciales mediante el certificado que está almacenado en el almacén de la máquina local y se identifique mediante su huella digital.</span><span class="sxs-lookup"><span data-stu-id="aee11-206">A *.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="aee11-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) se aplica al archivo *.meta.mof.</span><span class="sxs-lookup"><span data-stu-id="aee11-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applies the *.meta.mof file.</span></span>
 * <span data-ttu-id="aee11-208">Un archivo MOF que aplica realmente la configuración.</span><span class="sxs-lookup"><span data-stu-id="aee11-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="aee11-209">Start-DscConfiguration aplica la configuración.</span><span class="sxs-lookup"><span data-stu-id="aee11-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="aee11-210">Estos comandos llevará a cabo esos pasos:</span><span class="sxs-lookup"><span data-stu-id="aee11-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="aee11-211">En este ejemplo se insertaría la configuración de DSC en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="aee11-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="aee11-212">La configuración de DSC también se puede aplicar mediante un servidor de incorporación de cambios de DSC, si está disponible.</span><span class="sxs-lookup"><span data-stu-id="aee11-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="aee11-213">Consulte [Setting up a DSC pull client](pullClient.md) (Configuración de un cliente de extracción de DSC) para obtener más información sobre cómo aplicar configuraciones de DSC mediante un servidor de incorporación de cambios de DSC.</span><span class="sxs-lookup"><span data-stu-id="aee11-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="aee11-214">Ejemplo de módulo de cifrado de credenciales</span><span class="sxs-lookup"><span data-stu-id="aee11-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="aee11-215">Este es un ejemplo completo que incorpora todos estos pasos, además de un cmdlet de aplicación auxiliar que exporta y copia las claves públicas:</span><span class="sxs-lookup"><span data-stu-id="aee11-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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

