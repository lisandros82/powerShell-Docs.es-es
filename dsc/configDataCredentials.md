---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Opciones de credenciales en los datos de configuración
ms.openlocfilehash: 3f1c75c65b357220856dd8e50694eb77808dee41
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="1da30-103">Opciones de credenciales en los datos de configuración</span><span class="sxs-lookup"><span data-stu-id="1da30-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="1da30-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1da30-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="1da30-105">Contraseñas de texto sin formato y usuarios del dominio</span><span class="sxs-lookup"><span data-stu-id="1da30-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="1da30-106">Las configuraciones DSC que contienen una credencial sin cifrado generarán un mensaje de error sobre contraseñas de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="1da30-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="1da30-107">Además, DSC generará una advertencia cuando se usen credenciales de dominio.</span><span class="sxs-lookup"><span data-stu-id="1da30-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="1da30-108">Para suprimir estos mensajes de advertencia y de error, utilice las palabras clave de datos de configuración DSC:</span><span class="sxs-lookup"><span data-stu-id="1da30-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="1da30-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="1da30-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="1da30-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="1da30-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="1da30-111">En general, no es seguro almacenar o transmitir contraseñas de texto sin formato y no cifradas.</span><span class="sxs-lookup"><span data-stu-id="1da30-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="1da30-112">Se recomienda proteger las credenciales mediante el uso de las técnicas que se describirán más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="1da30-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="1da30-113">El servicio DSC de Azure Automation le permite administrar de forma centralizada las credenciales que se deben compilar en las configuraciones y almacenar de forma segura.</span><span class="sxs-lookup"><span data-stu-id="1da30-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="1da30-114">Para obtener información, vea los artículos [Compilación de configuraciones DSC y Recursos de credenciales](/azure/automation/automation-dsc-compile#credential-assets).</span><span class="sxs-lookup"><span data-stu-id="1da30-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="1da30-115">A continuación se muestra un ejemplo de transferencia de credenciales de texto sin formato:</span><span class="sxs-lookup"><span data-stu-id="1da30-115">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="1da30-116">Control de credenciales en DSC</span><span class="sxs-lookup"><span data-stu-id="1da30-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="1da30-117">Los recursos de configuración DSC se ejecutan como `Local System` de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="1da30-117">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="1da30-118">Sin embargo, algunos recursos necesitan una credencial, por ejemplo cuando el recurso `Package` necesita instalar software en una cuenta de usuario concreta.</span><span class="sxs-lookup"><span data-stu-id="1da30-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="1da30-119">Los recursos anteriores utilizaban un nombre de propiedad `Credential` codificado de forma rígida para controlar esto.</span><span class="sxs-lookup"><span data-stu-id="1da30-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="1da30-120">WMF 5.0 agregó una propiedad `PsDscRunAsCredential` automática para todos los recursos.</span><span class="sxs-lookup"><span data-stu-id="1da30-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="1da30-121">Para obtener más información sobre cómo usar `PsDscRunAsCredential`, vea [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="1da30-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="1da30-122">Los recursos más recientes y los recursos personalizados pueden utilizar esta propiedad automática en lugar de crear su propia propiedad para las credenciales.</span><span class="sxs-lookup"><span data-stu-id="1da30-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="1da30-123">El diseño de algunos recursos implica que se van a usar varias credenciales para un motivo concreto y tendrán sus propias propiedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="1da30-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="1da30-124">Para encontrar las propiedades de credenciales disponibles en un recurso, use `Get-DscResource -Name ResourceName -Syntax` o Intellisense en el ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="1da30-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="1da30-125">En este ejemplo se utiliza un recurso [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) del módulo de recursos integrado de DSC `PSDesiredStateConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="1da30-125">This example uses a [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="1da30-126">Puede crear grupos locales y agregar o quitar miembros.</span><span class="sxs-lookup"><span data-stu-id="1da30-126">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="1da30-127">Acepta tanto la propiedad `Credential` como la propiedad automática `PsDscRunAsCredential`.</span><span class="sxs-lookup"><span data-stu-id="1da30-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="1da30-128">No obstante, el recurso solo utiliza la propiedad `Credential`.</span><span class="sxs-lookup"><span data-stu-id="1da30-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="1da30-129">Para más información sobre la propiedad `PsDscRunAsCredential`, consulte [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="1da30-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="1da30-130">Ejemplo: la propiedad Credential del recurso Group</span><span class="sxs-lookup"><span data-stu-id="1da30-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="1da30-131">DSC se ejecuta en `Local System`, por lo que ya tiene permisos para cambiar grupos y usuarios locales.</span><span class="sxs-lookup"><span data-stu-id="1da30-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="1da30-132">Si el miembro agregado es una cuenta local, no se necesitan credenciales.</span><span class="sxs-lookup"><span data-stu-id="1da30-132">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="1da30-133">Si el recurso `Group` agrega una cuenta de dominio al grupo local, es necesaria una credencial.</span><span class="sxs-lookup"><span data-stu-id="1da30-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="1da30-134">No se permiten las consultas anónimas a Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1da30-134">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="1da30-135">La propiedad `Credential` del recurso `Group` es la cuenta de dominio que se utiliza para consultar a Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1da30-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="1da30-136">En la mayoría de casos esto podría deberse a una cuenta de usuario genérica ya que, de forma predeterminada, los usuarios pueden *leer* la mayoría de objetos de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1da30-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="1da30-137">Configuración de ejemplo</span><span class="sxs-lookup"><span data-stu-id="1da30-137">Example Configuration</span></span>

<span data-ttu-id="1da30-138">En el ejemplo de código siguiente se utiliza DSC para rellenar un grupo local con un usuario de dominio:</span><span class="sxs-lookup"><span data-stu-id="1da30-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="1da30-139">Este código genera un error y un mensaje de advertencia:</span><span class="sxs-lookup"><span data-stu-id="1da30-139">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="1da30-140">Este ejemplo tiene dos problemas:</span><span class="sxs-lookup"><span data-stu-id="1da30-140">This example has two issues:</span></span>
1. <span data-ttu-id="1da30-141">Un error explica que no se recomiendan las contraseñas de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="1da30-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="1da30-142">Una advertencia recomienda que no se use una credencial de dominio.</span><span class="sxs-lookup"><span data-stu-id="1da30-142">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="1da30-143">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="1da30-143">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="1da30-144">El primer mensaje de error tiene una dirección URL con documentación.</span><span class="sxs-lookup"><span data-stu-id="1da30-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="1da30-145">En este vínculo se explica cómo cifrar contraseñas con una estructura [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) y un certificado.</span><span class="sxs-lookup"><span data-stu-id="1da30-145">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="1da30-146">Para más información sobre certificados y DSC, [lea esta publicación](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="1da30-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="1da30-147">Para forzar una contraseña de texto sin formato, el recurso requiere la palabra clave `PsDscAllowPlainTextPassword` en la sección de datos de configuración, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="1da30-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="1da30-148">`NodeName` no puede ser igual a asterisco, es obligatorio un nombre de nodo específico.</span><span class="sxs-lookup"><span data-stu-id="1da30-148">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="1da30-149">**Microsoft aconseja evitar las contraseñas de texto sin formato por sus riesgos de seguridad considerables.**</span><span class="sxs-lookup"><span data-stu-id="1da30-149">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

<span data-ttu-id="1da30-150">Se produciría una excepción al usar el servicio DSC de Azure Automation solo porque los datos se almacenan siempre cifrados (en tránsito, en reposo en el servicio y en reposo en el nodo).</span><span class="sxs-lookup"><span data-stu-id="1da30-150">An exception would be when using the Azure Automation DSC service, only because the data is always stored encrypted (in transit, at rest in the service, and at rest on the node).</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="1da30-151">Credenciales de dominio</span><span class="sxs-lookup"><span data-stu-id="1da30-151">Domain Credentials</span></span>

<span data-ttu-id="1da30-152">Si se ejecuta de nuevo el script de configuración de ejemplo (con o sin cifrado), se sigue generando la advertencia que indica que no se recomienda el uso de una cuenta de dominio para una credencial.</span><span class="sxs-lookup"><span data-stu-id="1da30-152">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="1da30-153">Si se utiliza una cuenta local, se elimina la posible exposición de credenciales de dominio podría usarse en otros servidores.</span><span class="sxs-lookup"><span data-stu-id="1da30-153">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="1da30-154">**Cuando se usan credenciales con recursos de DSC, siempre que sea posible es preferible usar una cuenta local en lugar de una cuenta de dominio.**</span><span class="sxs-lookup"><span data-stu-id="1da30-154">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="1da30-155">Si hay un carácter '\'' o '\@' en la propiedad `Username` de la credencial, DSC lo tratará como una cuenta de dominio.</span><span class="sxs-lookup"><span data-stu-id="1da30-155">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="1da30-156">Existen excepciones para "localhost", "127.0.0.1" y "::1" en la parte del dominio del nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="1da30-156">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="1da30-157">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="1da30-157">PSDscAllowDomainUser</span></span>

<span data-ttu-id="1da30-158">En el ejemplo del recurso `Group` de DSC anterior, la consulta a un dominio de Active Directory *requiere* una cuenta de dominio.</span><span class="sxs-lookup"><span data-stu-id="1da30-158">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="1da30-159">En este caso, agregue la propiedad `PSDscAllowDomainUser` al bloque `ConfigurationData` como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="1da30-159">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="1da30-160">Ahora, el script de configuración generará el archivo MOF sin errores ni advertencias.</span><span class="sxs-lookup"><span data-stu-id="1da30-160">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>