---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: Configuración de un servidor de incorporación de cambios SMB de DSC
ms.openlocfilehash: 25705d9ae06b3ce8daa352142cc0b84793ab6359
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324858"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="b5429-103">Configuración de un servidor de incorporación de cambios SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="b5429-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="b5429-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b5429-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5429-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b5429-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b5429-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b5429-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b5429-107">Un servidor de extracción [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) de DSC es un equipo que hospeda recursos compartidos de archivos SMB que ponen los archivos de configuración de DSC o los recursos de DSC a disposición de los nodos de destino cuando estos nodos los solicitan.</span><span class="sxs-lookup"><span data-stu-id="b5429-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b5429-108">Para utilizar un servidor de incorporación de cambios SMB para DSC, debe:</span><span class="sxs-lookup"><span data-stu-id="b5429-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="b5429-109">Configurar un recurso compartido de archivos SMB en un servidor que ejecute PowerShell 4.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="b5429-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="b5429-110">Configurar un cliente que ejecute PowerShell 4.0 o posterior para que se extraiga de ese recurso compartido SMB</span><span class="sxs-lookup"><span data-stu-id="b5429-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="b5429-111">Usar el recurso xSmbShare para crear un recurso compartido de archivos SMB</span><span class="sxs-lookup"><span data-stu-id="b5429-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="b5429-112">Hay varias maneras de configurar un recurso compartido de archivos SMB, pero echemos un vistazo a cómo puede hacerlo mediante DSC.</span><span class="sxs-lookup"><span data-stu-id="b5429-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="b5429-113">Instalar el recurso xSmbShare</span><span class="sxs-lookup"><span data-stu-id="b5429-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="b5429-114">Llame al cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar el módulo **xSmbShare**</span><span class="sxs-lookup"><span data-stu-id="b5429-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="b5429-115">`Install-Module` está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b5429-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b5429-116">Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="b5429-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="b5429-117">**xSmbShare** contiene el recurso de DSC **xSmbShare**, que se puede usar para crear un recurso compartido de archivos SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="b5429-118">Crear el directorio y el recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="b5429-118">Create the directory and file share</span></span>

<span data-ttu-id="b5429-119">La configuración siguiente utiliza el recurso **File** para crear el directorio para el recurso compartido, y el recurso **xSmbShare** para configurar el recurso compartido SMB:</span><span class="sxs-lookup"><span data-stu-id="b5429-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="b5429-120">La configuración crea el directorio `C:\DscSmbShare` si aún no existe y, a continuación, usa ese directorio como un recurso compartido de archivos SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="b5429-121">**FullAccess** debe proporcionarse a cualquier cuenta que deba escribir o eliminar contenido del recurso compartido de archivo.</span><span class="sxs-lookup"><span data-stu-id="b5429-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="b5429-122">**ReadAccess** debe proporcionarse a cualquier nodo de cliente que obtenga configuraciones o recursos de DSC del recurso compartido.</span><span class="sxs-lookup"><span data-stu-id="b5429-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="b5429-123">DSC se ejecuta como la cuenta del sistema de forma predeterminada, por lo que el mismo equipo debe tener acceso al recurso compartido.</span><span class="sxs-lookup"><span data-stu-id="b5429-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="b5429-124">Conceder al sistema de archivos acceso al cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="b5429-124">Give file system access to the pull client</span></span>

<span data-ttu-id="b5429-125">Al conceder el acceso **ReadAccess** a un nodo de cliente, se permite que ese nodo acceda al recurso compartido SMB, pero no a los archivos o a las carpetas de dentro de ese recurso compartido.</span><span class="sxs-lookup"><span data-stu-id="b5429-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="b5429-126">Tiene que conceder explícitamente a los nodos de cliente acceso a las carpetas y subcarpetas del recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="b5429-127">Se puede hacer esto con DSC si se agrega con el recurso **cNtfsPermissionEntry**, que se encuentra en el módulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).</span><span class="sxs-lookup"><span data-stu-id="b5429-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="b5429-128">La siguiente configuración agrega un bloque **cNtfsPermissionEntry** que concede acceso ReadAndExecute al cliente de incorporación de cambios:</span><span class="sxs-lookup"><span data-stu-id="b5429-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b5429-129">Colocación de configuraciones y recursos</span><span class="sxs-lookup"><span data-stu-id="b5429-129">Placing configurations and resources</span></span>

<span data-ttu-id="b5429-130">Guarde todos los archivos MOF de configuración o los recursos de DSC que quiera que los nodos de cliente extraigan en la carpeta del recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="b5429-131">Todos los archivos MOF de configuración deben denominarse *ConfigurationID*.mof, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="b5429-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="b5429-132">Para más información sobre la configuración de clientes de extracción, vea [Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="b5429-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b5429-133">Debe usar identificadores de configuración si está utilizando un servidor de incorporación de cambios SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="b5429-134">Los nombres de configuración no son compatibles con SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="b5429-135">Cada módulo de recursos se debe comprimir y se le debe asignar un nombre de acuerdo con el patrón `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="b5429-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="b5429-136">Por ejemplo, un módulo denominado xWebAdminstration con una versión de módulo de 3.1.2.0 se denominaría 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="b5429-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="b5429-137">Cada versión de un módulo debe incluirse en un solo archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="b5429-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="b5429-138">No se admiten versiones distintas de un módulo en un archivo zip.</span><span class="sxs-lookup"><span data-stu-id="b5429-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="b5429-139">Antes de empaquetar los módulos de recursos de DSC para su uso con el servidor de extracción, debe realizar un pequeño cambio en la estructura de directorios.</span><span class="sxs-lookup"><span data-stu-id="b5429-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="b5429-140">El formato predeterminado de los módulos que contienen recursos de DSC en WMF 5.0 es `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="b5429-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="b5429-141">Antes de empaquetar para el servidor de incorporación de cambios, simplemente quite la carpeta `{Module version}` para que la ruta se quede en `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="b5429-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="b5429-142">Con este cambio, comprima la carpeta según lo descrito anteriormente y coloque estos archivos ZIP en la carpeta compartida SMB.</span><span class="sxs-lookup"><span data-stu-id="b5429-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="b5429-143">Creación de la suma de comprobación MOF</span><span class="sxs-lookup"><span data-stu-id="b5429-143">Creating the MOF checksum</span></span>

<span data-ttu-id="b5429-144">Un archivo de configuración MOF debe emparejarse con un archivo de suma de comprobación para que un LCM de un nodo de destino pueda validar la configuración.</span><span class="sxs-lookup"><span data-stu-id="b5429-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b5429-145">Para crear una suma de comprobación, llame al cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum).</span><span class="sxs-lookup"><span data-stu-id="b5429-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="b5429-146">El cmdlet toma un parámetro `Path` que especifica la carpeta donde se encuentra el MOF de configuración.</span><span class="sxs-lookup"><span data-stu-id="b5429-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="b5429-147">El cmdlet crea un archivo de suma de comprobación denominado `ConfigurationMOFName.mof.checksum`, donde `ConfigurationMOFName` es el nombre del archivo mof de configuración.</span><span class="sxs-lookup"><span data-stu-id="b5429-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b5429-148">Si hay más de un archivo MOF de configuración en la carpeta especificada, se crea una suma de comprobación para cada una de las configuraciones de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="b5429-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="b5429-149">El archivo de suma de comprobación debe estar en el mismo directorio que el archivo MOF de configuración (de forma predeterminada, `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`) y tener el mismo nombre con la extensión `.checksum` anexada.</span><span class="sxs-lookup"><span data-stu-id="b5429-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="b5429-150">Si cambia el archivo MOF de configuración de cualquier manera, también deberá volver a crear el archivo de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="b5429-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="b5429-151">Configuración de un cliente de extracción para SMB</span><span class="sxs-lookup"><span data-stu-id="b5429-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="b5429-152">Para configurar un cliente que extraiga las configuraciones o recursos desde un recurso compartido de SMB, configure el administrador de configuración local (LCM) del cliente con los bloques **ConfigurationRepositoryShare** y **ResourceRepositoryShare** que especifiquen el recurso compartido desde el que se van a extraer las configuraciones y los recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="b5429-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="b5429-153">Para obtener más información sobre cómo configurar el LCM, consulte [Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="b5429-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b5429-154">Por motivos de simplicidad, este ejemplo usa **PSDscAllowPlainTextPassword** para permitir pasar una contraseña de texto no cifrado al parámetro **Credential**.</span><span class="sxs-lookup"><span data-stu-id="b5429-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="b5429-155">Para obtener información sobre cómo pasar credenciales de forma más segura, consulte [Opciones de credenciales en los datos de configuración](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b5429-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="b5429-156">**DEBE** especificar un **ConfigurationID** en el bloque **Configuration** de una metaconfiguración para un servidor de incorporación de cambios SMB, incluso si solo está incorporando recursos.</span><span class="sxs-lookup"><span data-stu-id="b5429-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="b5429-157">Agradecimientos</span><span class="sxs-lookup"><span data-stu-id="b5429-157">Acknowledgements</span></span>

<span data-ttu-id="b5429-158">Agradecimientos especiales a las personas siguientes:</span><span class="sxs-lookup"><span data-stu-id="b5429-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="b5429-159">Mike F. Robbins, cuyas publicaciones sobre el uso de SMB para DSC permitieron informar del contenido de este tema.</span><span class="sxs-lookup"><span data-stu-id="b5429-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="b5429-160">Su blog es [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="b5429-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="b5429-161">Serge Nikalaichyk, que creó el módulo **cNtfsAccessControl**.</span><span class="sxs-lookup"><span data-stu-id="b5429-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="b5429-162">El código de este módulo está en [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="b5429-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5429-163">Vea también</span><span class="sxs-lookup"><span data-stu-id="b5429-163">See also</span></span>

[<span data-ttu-id="b5429-164">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5429-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="b5429-165">Establecer configuraciones</span><span class="sxs-lookup"><span data-stu-id="b5429-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="b5429-166">Configuración de un cliente de extracción mediante id. de configuración</span><span class="sxs-lookup"><span data-stu-id="b5429-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
