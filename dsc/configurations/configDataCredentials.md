---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Opciones de credenciales en los datos de configuración
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046648"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="7963f-103">Opciones de credenciales en los datos de configuración</span><span class="sxs-lookup"><span data-stu-id="7963f-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="7963f-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7963f-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="7963f-105">Contraseñas de texto sin formato y usuarios del dominio</span><span class="sxs-lookup"><span data-stu-id="7963f-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="7963f-106">Las configuraciones DSC que contienen una credencial sin cifrado generarán un mensaje de error sobre contraseñas de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="7963f-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="7963f-107">Además, DSC generará una advertencia cuando se usen credenciales de dominio.</span><span class="sxs-lookup"><span data-stu-id="7963f-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="7963f-108">Para suprimir estos mensajes de advertencia y de error, utilice las palabras clave de datos de configuración DSC:</span><span class="sxs-lookup"><span data-stu-id="7963f-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="7963f-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="7963f-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="7963f-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="7963f-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="7963f-111">En general, no es seguro almacenar o transmitir contraseñas de texto sin formato y no cifradas.</span><span class="sxs-lookup"><span data-stu-id="7963f-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="7963f-112">Se recomienda proteger las credenciales mediante el uso de las técnicas que se describirán más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="7963f-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="7963f-113">El servicio DSC de Azure Automation le permite administrar de forma centralizada las credenciales que se deben compilar en las configuraciones y almacenar de forma segura.</span><span class="sxs-lookup"><span data-stu-id="7963f-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="7963f-114">Para obtener información, consulte: [Compilación de configuraciones de DSC / recursos de credenciales](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="7963f-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="7963f-115">A continuación se muestra un ejemplo de transferencia de credenciales de texto sin formato:</span><span class="sxs-lookup"><span data-stu-id="7963f-115">The following is an example of passing plain text credentials:</span></span>

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="7963f-116">Esto es un extracto del archivo "MOF" generado por la configuración de "TestMachine1".</span><span class="sxs-lookup"><span data-stu-id="7963f-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="7963f-117">El `System.Security.SecureString` usado en la configuración se puede convertir en texto sin formato y se almacenó en el archivo "MOF" como un `MSF_Credential`.</span><span class="sxs-lookup"><span data-stu-id="7963f-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="7963f-118">Un `SecureString` se cifra con el perfil del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="7963f-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="7963f-119">Esto funciona bien con todas las formas de administración remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7963f-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="7963f-120">Un archivo ".mof" está diseñado como un mecanismo de configuración por sí sola independiente.</span><span class="sxs-lookup"><span data-stu-id="7963f-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="7963f-121">A partir de PowerShell 5.0, los archivos de "MOF" en un nodo se cifran en reposo, pero no en tránsito al nodo.</span><span class="sxs-lookup"><span data-stu-id="7963f-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="7963f-122">Esto significa que las contraseñas en un archivo ".mof" se exponen como texto no cifrado al aplicar a un nodo.</span><span class="sxs-lookup"><span data-stu-id="7963f-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="7963f-123">Para cifrar las credenciales, deberá usar un **servidor de extracción**.</span><span class="sxs-lookup"><span data-stu-id="7963f-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="7963f-124">Para obtener más información, consulte [archivos MOF de protección con certificados](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="7963f-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="7963f-125">Control de credenciales en DSC</span><span class="sxs-lookup"><span data-stu-id="7963f-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="7963f-126">Los recursos de configuración DSC se ejecutan como `Local System` de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="7963f-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="7963f-127">Sin embargo, algunos recursos necesitan una credencial, por ejemplo cuando el recurso `Package` necesita instalar software en una cuenta de usuario concreta.</span><span class="sxs-lookup"><span data-stu-id="7963f-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="7963f-128">Los recursos anteriores utilizaban un nombre de propiedad `Credential` codificado de forma rígida para controlar esto.</span><span class="sxs-lookup"><span data-stu-id="7963f-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="7963f-129">WMF 5.0 agregó una propiedad `PsDscRunAsCredential` automática para todos los recursos.</span><span class="sxs-lookup"><span data-stu-id="7963f-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="7963f-130">Para obtener más información sobre cómo usar `PsDscRunAsCredential`, vea [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="7963f-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="7963f-131">Los recursos más recientes y los recursos personalizados pueden utilizar esta propiedad automática en lugar de crear su propia propiedad para las credenciales.</span><span class="sxs-lookup"><span data-stu-id="7963f-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="7963f-132">El diseño de algunos recursos implica que se van a usar varias credenciales para un motivo concreto y tendrán sus propias propiedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="7963f-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="7963f-133">Para encontrar las propiedades de credenciales disponibles en un recurso, use `Get-DscResource -Name ResourceName -Syntax` o Intellisense en el ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="7963f-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="7963f-134">En este ejemplo se utiliza un recurso [Group](../resources/resources.md) del módulo de recursos integrado de DSC `PSDesiredStateConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="7963f-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="7963f-135">Puede crear grupos locales y agregar o quitar miembros.</span><span class="sxs-lookup"><span data-stu-id="7963f-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="7963f-136">Acepta tanto la propiedad `Credential` como la propiedad automática `PsDscRunAsCredential`.</span><span class="sxs-lookup"><span data-stu-id="7963f-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="7963f-137">No obstante, el recurso solo utiliza la propiedad `Credential`.</span><span class="sxs-lookup"><span data-stu-id="7963f-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="7963f-138">Para más información sobre la propiedad `PsDscRunAsCredential`, consulte [DSC de ejecución con las credenciales de usuario](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="7963f-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="7963f-139">Ejemplo: La propiedad Credential del recurso de grupo</span><span class="sxs-lookup"><span data-stu-id="7963f-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="7963f-140">DSC se ejecuta en `Local System`, por lo que ya tiene permisos para cambiar grupos y usuarios locales.</span><span class="sxs-lookup"><span data-stu-id="7963f-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="7963f-141">Si el miembro agregado es una cuenta local, no se necesitan credenciales.</span><span class="sxs-lookup"><span data-stu-id="7963f-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="7963f-142">Si el recurso `Group` agrega una cuenta de dominio al grupo local, es necesaria una credencial.</span><span class="sxs-lookup"><span data-stu-id="7963f-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="7963f-143">No se permiten las consultas anónimas a Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7963f-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="7963f-144">La propiedad `Credential` del recurso `Group` es la cuenta de dominio que se utiliza para consultar a Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7963f-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="7963f-145">En la mayoría de casos esto podría deberse a una cuenta de usuario genérica ya que, de forma predeterminada, los usuarios pueden *leer* la mayoría de objetos de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7963f-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="7963f-146">Configuración de ejemplo</span><span class="sxs-lookup"><span data-stu-id="7963f-146">Example Configuration</span></span>

<span data-ttu-id="7963f-147">En el ejemplo de código siguiente se utiliza DSC para rellenar un grupo local con un usuario de dominio:</span><span class="sxs-lookup"><span data-stu-id="7963f-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="7963f-148">Este código genera un error y un mensaje de advertencia:</span><span class="sxs-lookup"><span data-stu-id="7963f-148">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="7963f-149">Este ejemplo tiene dos problemas:</span><span class="sxs-lookup"><span data-stu-id="7963f-149">This example has two issues:</span></span>
1. <span data-ttu-id="7963f-150">Un error explica que no se recomiendan las contraseñas de texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="7963f-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="7963f-151">Una advertencia recomienda que no se use una credencial de dominio.</span><span class="sxs-lookup"><span data-stu-id="7963f-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="7963f-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="7963f-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="7963f-153">El primer mensaje de error tiene una dirección URL con documentación.</span><span class="sxs-lookup"><span data-stu-id="7963f-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="7963f-154">En este vínculo se explica cómo cifrar contraseñas con una estructura [ConfigurationData](./configData.md) y un certificado.</span><span class="sxs-lookup"><span data-stu-id="7963f-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="7963f-155">Para más información sobre certificados y DSC, [lea esta publicación](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="7963f-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="7963f-156">Para forzar una contraseña de texto sin formato, el recurso requiere la palabra clave `PsDscAllowPlainTextPassword` en la sección de datos de configuración, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="7963f-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="7963f-157">`NodeName` no puede ser igual a asterisco, es obligatorio un nombre de nodo específico.</span><span class="sxs-lookup"><span data-stu-id="7963f-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="7963f-158">**Microsoft aconseja evitar las contraseñas de texto sin formato por sus riesgos de seguridad considerables.**</span><span class="sxs-lookup"><span data-stu-id="7963f-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="7963f-159">Credenciales de dominio</span><span class="sxs-lookup"><span data-stu-id="7963f-159">Domain Credentials</span></span>

<span data-ttu-id="7963f-160">Si se ejecuta de nuevo el script de configuración de ejemplo (con o sin cifrado), se sigue generando la advertencia que indica que no se recomienda el uso de una cuenta de dominio para una credencial.</span><span class="sxs-lookup"><span data-stu-id="7963f-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="7963f-161">Si se utiliza una cuenta local, se elimina la posible exposición de credenciales de dominio podría usarse en otros servidores.</span><span class="sxs-lookup"><span data-stu-id="7963f-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="7963f-162">**Cuando se usan credenciales con recursos de DSC, siempre que sea posible es preferible usar una cuenta local en lugar de una cuenta de dominio.**</span><span class="sxs-lookup"><span data-stu-id="7963f-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="7963f-163">Si hay un carácter '\'' o '@' en la propiedad `Username` de la credencial, DSC lo tratará como una cuenta de dominio.</span><span class="sxs-lookup"><span data-stu-id="7963f-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="7963f-164">Existen excepciones para "localhost", "127.0.0.1" y "::1" en la parte del dominio del nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="7963f-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="7963f-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="7963f-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="7963f-166">En el ejemplo del recurso `Group` de DSC anterior, la consulta a un dominio de Active Directory *requiere* una cuenta de dominio.</span><span class="sxs-lookup"><span data-stu-id="7963f-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="7963f-167">En este caso, agregue la propiedad `PSDscAllowDomainUser` al bloque `ConfigurationData` como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="7963f-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="7963f-168">Ahora, el script de configuración generará el archivo MOF sin errores ni advertencias.</span><span class="sxs-lookup"><span data-stu-id="7963f-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
