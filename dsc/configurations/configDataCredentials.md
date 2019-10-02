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
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="54db4-103">Opciones de credenciales en los datos de configuración</span><span class="sxs-lookup"><span data-stu-id="54db4-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="54db4-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="54db4-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="54db4-105">Contraseñas de texto sin formato y usuarios del dominio</span><span class="sxs-lookup"><span data-stu-id="54db4-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="54db4-106">Las configuraciones DSC que contienen una credencial sin cifrado generarán un mensaje de error sobre contraseñas de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="54db4-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="54db4-107">Además, DSC generará una advertencia cuando se usen credenciales de dominio.</span><span class="sxs-lookup"><span data-stu-id="54db4-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="54db4-108">Para suprimir estos mensajes de advertencia y de error, utilice las palabras clave de datos de configuración DSC:</span><span class="sxs-lookup"><span data-stu-id="54db4-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="54db4-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="54db4-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="54db4-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="54db4-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="54db4-111">En general, no es seguro almacenar o transmitir contraseñas de texto sin formato y no cifradas.</span><span class="sxs-lookup"><span data-stu-id="54db4-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="54db4-112">Se recomienda proteger las credenciales mediante el uso de las técnicas que se describirán más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="54db4-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="54db4-113">El servicio DSC de Azure Automation le permite administrar de forma centralizada las credenciales que se deben compilar en las configuraciones y almacenar de forma segura.</span><span class="sxs-lookup"><span data-stu-id="54db4-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="54db4-114">Para obtener información, consulte: [Compilación de configuraciones DSC y Recursos de credenciales](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="54db4-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="54db4-115">Control de credenciales en DSC</span><span class="sxs-lookup"><span data-stu-id="54db4-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="54db4-116">Los recursos de configuración DSC se ejecutan como `Local System` de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="54db4-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="54db4-117">Sin embargo, algunos recursos necesitan una credencial, por ejemplo cuando el recurso `Package` necesita instalar software en una cuenta de usuario concreta.</span><span class="sxs-lookup"><span data-stu-id="54db4-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="54db4-118">Los recursos anteriores utilizaban un nombre de propiedad `Credential` codificado de forma rígida para controlar esto.</span><span class="sxs-lookup"><span data-stu-id="54db4-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="54db4-119">WMF 5.0 agregó una propiedad `PsDscRunAsCredential` automática para todos los recursos.</span><span class="sxs-lookup"><span data-stu-id="54db4-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="54db4-120">Para obtener más información sobre cómo usar `PsDscRunAsCredential`, vea [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="54db4-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="54db4-121">Los recursos más recientes y los recursos personalizados pueden utilizar esta propiedad automática en lugar de crear su propia propiedad para las credenciales.</span><span class="sxs-lookup"><span data-stu-id="54db4-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="54db4-122">El diseño de algunos recursos implica que se van a usar varias credenciales para un motivo concreto y tendrán sus propias propiedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="54db4-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="54db4-123">Para encontrar las propiedades de credenciales disponibles en un recurso, use `Get-DscResource -Name ResourceName -Syntax` o Intellisense en el ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="54db4-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="54db4-124">En este ejemplo se utiliza un recurso [Group](../resources/resources.md) del módulo de recursos integrado de DSC `PSDesiredStateConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="54db4-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="54db4-125">Puede crear grupos locales y agregar o quitar miembros.</span><span class="sxs-lookup"><span data-stu-id="54db4-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="54db4-126">Acepta tanto la propiedad `Credential` como la propiedad automática `PsDscRunAsCredential`.</span><span class="sxs-lookup"><span data-stu-id="54db4-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="54db4-127">No obstante, el recurso solo utiliza la propiedad `Credential`.</span><span class="sxs-lookup"><span data-stu-id="54db4-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="54db4-128">Para más información sobre la propiedad `PsDscRunAsCredential`, consulte [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="54db4-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="54db4-129">Ejemplo: la propiedad Credential del recurso Group</span><span class="sxs-lookup"><span data-stu-id="54db4-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="54db4-130">DSC se ejecuta en `Local System`, por lo que ya tiene permisos para cambiar grupos y usuarios locales.</span><span class="sxs-lookup"><span data-stu-id="54db4-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="54db4-131">Si el miembro agregado es una cuenta local, no se necesitan credenciales.</span><span class="sxs-lookup"><span data-stu-id="54db4-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="54db4-132">Si el recurso `Group` agrega una cuenta de dominio al grupo local, es necesaria una credencial.</span><span class="sxs-lookup"><span data-stu-id="54db4-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="54db4-133">No se permiten las consultas anónimas a Active Directory.</span><span class="sxs-lookup"><span data-stu-id="54db4-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="54db4-134">La propiedad `Credential` del recurso `Group` es la cuenta de dominio que se utiliza para consultar a Active Directory.</span><span class="sxs-lookup"><span data-stu-id="54db4-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="54db4-135">En la mayoría de casos esto podría deberse a una cuenta de usuario genérica ya que, de forma predeterminada, los usuarios pueden *leer* la mayoría de objetos de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="54db4-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="54db4-136">Configuración de ejemplo</span><span class="sxs-lookup"><span data-stu-id="54db4-136">Example Configuration</span></span>

<span data-ttu-id="54db4-137">En el ejemplo de código siguiente se utiliza DSC para rellenar un grupo local con un usuario de dominio:</span><span class="sxs-lookup"><span data-stu-id="54db4-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="54db4-138">Este código genera un error y un mensaje de advertencia:</span><span class="sxs-lookup"><span data-stu-id="54db4-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="54db4-139">Este ejemplo tiene dos problemas:</span><span class="sxs-lookup"><span data-stu-id="54db4-139">This example has two issues:</span></span>

1. <span data-ttu-id="54db4-140">Un error explica que no se recomiendan las contraseñas de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="54db4-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="54db4-141">Una advertencia recomienda que no se use una credencial de dominio.</span><span class="sxs-lookup"><span data-stu-id="54db4-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="54db4-142">Las marcas de **PSDSCAllowPlainTextPassword** y **PSDSCAllowDomainUser** suprimen el error y la advertencia que informan al usuario del riesgo que conlleva.</span><span class="sxs-lookup"><span data-stu-id="54db4-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="54db4-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="54db4-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="54db4-144">El primer mensaje de error tiene una dirección URL con documentación.</span><span class="sxs-lookup"><span data-stu-id="54db4-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="54db4-145">En este vínculo se explica cómo cifrar contraseñas con una estructura [ConfigurationData](./configData.md) y un certificado.</span><span class="sxs-lookup"><span data-stu-id="54db4-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="54db4-146">Para más información sobre certificados y DSC, [lea esta publicación](https://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="54db4-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="54db4-147">Para forzar una contraseña de texto sin formato, el recurso requiere la palabra clave `PsDscAllowPlainTextPassword` en la sección de datos de configuración, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="54db4-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="54db4-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="54db4-148">localhost.mof</span></span>

<span data-ttu-id="54db4-149">La marca **PSDSCAllowPlainTextPassword** requiere que el usuario reconozca el riesgo de almacenar contraseñas de texto sin formato en un archivo MOF.</span><span class="sxs-lookup"><span data-stu-id="54db4-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="54db4-150">En el archivo MOF generado, aunque se utilizó un objeto **PSCredential** que contenía un valor **SecureString**, las contraseñas aún aparecen como texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="54db4-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="54db4-151">Esta es la única vez que se exponen las credenciales.</span><span class="sxs-lookup"><span data-stu-id="54db4-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="54db4-152">Al obtener acceso a este archivo MOF, cualquier persona puede acceder a la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="54db4-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="54db4-153">Credenciales en tránsito y en reposo</span><span class="sxs-lookup"><span data-stu-id="54db4-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="54db4-154">La marca **PSDscAllowPlainTextPassword** permite la compilación de archivos MOF que contienen contraseñas como texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="54db4-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="54db4-155">Tome precauciones cuando almacene archivos MOF que contienen contraseñas de texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="54db4-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="54db4-156">Cuando el archivo MOF se entrega a un nodo en modo de **inserción**, WinRM cifra la comunicación para proteger la contraseña de texto no cifrado a menos que reemplace el valor predeterminado por el parámetro **AllowUnencrypted**.</span><span class="sxs-lookup"><span data-stu-id="54db4-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="54db4-157">El cifrado del MOF con un certificado protege el archivo MOF en reposo antes de que se haya aplicado a un nodo.</span><span class="sxs-lookup"><span data-stu-id="54db4-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="54db4-158">En el modo de **extracción**, puede configurar el servidor de extracción de Windows para usar HTTPS para el cifrado del tráfico mediante el protocolo especificado en Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="54db4-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="54db4-159">Para obtener más información, consulte los artículos [Configuración de un cliente de extracción de DSC](../pull-server/pullclient.md) y [Proteger el archivo MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="54db4-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="54db4-160">En el servicio [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview), siempre se cifra el tráfico de extracción.</span><span class="sxs-lookup"><span data-stu-id="54db4-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="54db4-161">En el nodo, los archivos MOF se cifran en reposo a partir de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="54db4-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="54db4-162">En PowerShell 4.0, los archivos MOF no se cifran en reposo, a menos que se cifrasen con un certificado cuando se insertaron en el nodo o se extrajeron de él.</span><span class="sxs-lookup"><span data-stu-id="54db4-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="54db4-163">**Microsoft aconseja evitar las contraseñas de texto sin formato por sus riesgos de seguridad considerables.**</span><span class="sxs-lookup"><span data-stu-id="54db4-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="54db4-164">Credenciales de dominio</span><span class="sxs-lookup"><span data-stu-id="54db4-164">Domain Credentials</span></span>

<span data-ttu-id="54db4-165">Si se ejecuta de nuevo el script de configuración de ejemplo (con o sin cifrado), se sigue generando la advertencia que indica que no se recomienda el uso de una cuenta de dominio para una credencial.</span><span class="sxs-lookup"><span data-stu-id="54db4-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="54db4-166">Si se utiliza una cuenta local, se elimina la posible exposición de credenciales de dominio podría usarse en otros servidores.</span><span class="sxs-lookup"><span data-stu-id="54db4-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="54db4-167">**Cuando se usan credenciales con recursos de DSC, siempre que sea posible es preferible usar una cuenta local en lugar de una cuenta de dominio.**</span><span class="sxs-lookup"><span data-stu-id="54db4-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="54db4-168">Si hay un carácter '\\' o '\@' en la propiedad `Username` de la credencial, DSC lo tratará como una cuenta de dominio.</span><span class="sxs-lookup"><span data-stu-id="54db4-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="54db4-169">Existen excepciones para "localhost", "127.0.0.1" y "::1" en la parte del dominio del nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="54db4-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="54db4-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="54db4-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="54db4-171">En el ejemplo del recurso `Group` de DSC anterior, la consulta a un dominio de Active Directory *requiere* una cuenta de dominio.</span><span class="sxs-lookup"><span data-stu-id="54db4-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="54db4-172">En este caso, agregue la propiedad `PSDscAllowDomainUser` al bloque `ConfigurationData` como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="54db4-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="54db4-173">Ahora, el script de configuración generará el archivo MOF sin errores ni advertencias.</span><span class="sxs-lookup"><span data-stu-id="54db4-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
