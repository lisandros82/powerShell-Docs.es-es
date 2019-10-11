---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuraciones parciales de la configuración de estado deseado de PowerShell
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955192"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="15930-103">Configuraciones parciales de la configuración de estado deseado de PowerShell</span><span class="sxs-lookup"><span data-stu-id="15930-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="15930-104">_Se aplica a: Windows PowerShell 5.0 y posterior._</span><span class="sxs-lookup"><span data-stu-id="15930-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="15930-105">En PowerShell 5.0, la configuración de estado deseado (DSC) permite que las configuraciones se entreguen en fragmentos y desde varios orígenes.</span><span class="sxs-lookup"><span data-stu-id="15930-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="15930-106">El administrador de configuración local (LCM) en el nodo de destino reúne los fragmentos antes de aplicarlos como una configuración única.</span><span class="sxs-lookup"><span data-stu-id="15930-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="15930-107">Esta capacidad permite compartir el control de la configuración entre equipos o usuarios.</span><span class="sxs-lookup"><span data-stu-id="15930-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="15930-108">Por ejemplo, si dos o más equipos de desarrolladores colaboran en un servicio, es posible que cada uno de ellos prefiera crear configuraciones para administrar su parte del servicio.</span><span class="sxs-lookup"><span data-stu-id="15930-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="15930-109">Cada una de estas configuraciones se podría extraer de servidores de extracción diferentes y se podría agregar en diferentes fases del desarrollo.</span><span class="sxs-lookup"><span data-stu-id="15930-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="15930-110">Las configuraciones parciales también permiten que distintas personas o equipos controlen aspectos diferentes de los nodos de configuración, sin tener que coordinar la edición de un documento de configuración único.</span><span class="sxs-lookup"><span data-stu-id="15930-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="15930-111">Por ejemplo, un equipo podría ser responsable de la implementación de una máquina virtual y un sistema operativo, mientras que otro equipo podría implementar otras aplicaciones y servicios en esa máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="15930-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="15930-112">Con las configuraciones parciales, cada equipo puede crear su propia configuración, sin que ninguna de ellas sea innecesariamente complicada.</span><span class="sxs-lookup"><span data-stu-id="15930-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="15930-113">Puede utilizar las configuraciones parciales en el modo de inserción, el modo de extracción o una combinación de ambos.</span><span class="sxs-lookup"><span data-stu-id="15930-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="15930-114">Configuraciones parciales en el modo de inserción</span><span class="sxs-lookup"><span data-stu-id="15930-114">Partial configurations in push mode</span></span>

<span data-ttu-id="15930-115">Para utilizar configuraciones parciales en modo de inserción, debe configurar el LCM en el nodo de destino para que reciba las configuraciones parciales.</span><span class="sxs-lookup"><span data-stu-id="15930-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="15930-116">Cada configuración parcial se debe insertar en el destino mediante el cmdlet `Publish-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="15930-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="15930-117">El nodo de destino combina entonces la configuración parcial en una configuración única, que puede aplicar mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="15930-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="15930-118">Configurar el LCM para configuraciones parcial del modo de inserción</span><span class="sxs-lookup"><span data-stu-id="15930-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="15930-119">Para configurar el LCM para configuraciones parciales en el modo de inserción, debe crear una configuración **DSCLocalConfigurationManager** con un bloque **PartialConfiguration** para cada configuración parcial.</span><span class="sxs-lookup"><span data-stu-id="15930-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="15930-120">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local de Windows](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="15930-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span> <span data-ttu-id="15930-121">En el ejemplo siguiente se muestra una configuración de LCM que espera dos configuraciones parciales: una que implemente el sistema operativo y otra que implemente y configure SharePoint.</span><span class="sxs-lookup"><span data-stu-id="15930-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="15930-122">El valor **RefreshMode** de cada configuración parcial se establece en "Push".</span><span class="sxs-lookup"><span data-stu-id="15930-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="15930-123">Los nombres de los bloques **PartialConfiguration** (en este caso, "ServiceAccountConfig" y "SharePointConfig") deben coincidir exactamente con los nombres de las configuraciones que se inserten en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="15930-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="15930-124">El nombre de cada bloque **PartialConfiguration** debe coincidir con el nombre real de la configuración tal como esté especificado en el script de configuración y no con el nombre del archivo MOF, que debe ser el nombre del nodo de destino o `localhost`.</span><span class="sxs-lookup"><span data-stu-id="15930-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="15930-125">Publicación e inicialización de las configuraciones parciales del modo de inserción</span><span class="sxs-lookup"><span data-stu-id="15930-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="15930-126">Después llame a [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) para cada configuración, pasando las carpetas que contengan los documentos de configuración como los parámetros **Path**.</span><span class="sxs-lookup"><span data-stu-id="15930-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="15930-127">`Publish-DSCConfiguration` coloca los archivos MOF de configuración en los nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="15930-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="15930-128">Después de publicar las dos configuraciones, puede llamar a `Start-DSCConfiguration –UseExisting` en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="15930-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="15930-129">Por ejemplo, si ha compilado los siguientes documentos MOF de configuración en el nodo de creación:</span><span class="sxs-lookup"><span data-stu-id="15930-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="15930-130">Publicaría y ejecutaría las configuraciones de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="15930-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="15930-131">El usuario que ejecuta el cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) debe tener privilegios de administrador en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="15930-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="15930-132">Configuraciones parciales en el modo de extracción</span><span class="sxs-lookup"><span data-stu-id="15930-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="15930-133">Las configuraciones parciales pueden extraerse de uno o varios servidores de extracción (para más información sobre los servidores de extracción, consulte [Servidores de extracción de la configuración de estado deseado de Windows PowerShell](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="15930-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="15930-134">Para ello, tendrá que configurar el LCM en el nodo de destino para extraer las configuraciones parciales, especificar un nombre y localizar los documentos de configuración correctamente en los servidores de extracción.</span><span class="sxs-lookup"><span data-stu-id="15930-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="15930-135">Configurar el LCM para configuraciones del modo de extracción</span><span class="sxs-lookup"><span data-stu-id="15930-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="15930-136">Para configurar el LCM para extraer configuraciones parciales de un servidor de extracción, debe definir el servidor de extracción en un bloque **ConfigurationRepositoryWeb** (para un servidor de extracción HTTP) o **ConfigurationRepositoryShare** (para un servidor de extracción SMB).</span><span class="sxs-lookup"><span data-stu-id="15930-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="15930-137">A continuación, cree bloques **PartialConfiguration** que hagan referencia al servidor de extracción mediante la propiedad **ConfigurationSource**.</span><span class="sxs-lookup"><span data-stu-id="15930-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="15930-138">También debe crear un bloque **Settings** para especificar que el LCM usa el modo de extracción y para especificar los valores de **ConfigurationNames** o **ConfigurationID** que el servidor de extracción y el nodo de destino usan para identificar las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="15930-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="15930-139">La metaconfiguración siguiente define un servidor de extracción HTTP denominado CONTOSO-PullSrv y dos configuraciones parciales que usan dicho servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="15930-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="15930-140">Para obtener más información sobre cómo configurar el LCM mediante **ConfigurationNames**, consulte [Configuración de un cliente de extracción mediante nombres de configuración](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="15930-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="15930-141">Para obtener más información sobre cómo configurar el LCM mediante **ConfigurationID**, consulte [Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="15930-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="15930-142">Configurar el LCM para configuraciones de modo de extracción mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="15930-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="15930-143">Configurar el LCM para configuraciones de modo de extracción mediante ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="15930-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="15930-144">Puede extraer configuraciones parciales de más de un servidor de extracción; solo sería necesario definir cada servidor de extracción y, después, hacer referencia al servidor de extracción adecuado en cada bloque **PartialConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="15930-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="15930-145">Después de crear la metaconfiguración, debe ejecutar para crear un documento de configuración (archivo MOF) y, a continuación, llame a [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) para configurar el LCM.</span><span class="sxs-lookup"><span data-stu-id="15930-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="15930-146">Nomenclatura y ubicación de los documentos de configuración en el servidor de extracción (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="15930-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="15930-147">Los documentos de configuración parcial deben ubicarse en la carpeta especificada en el valor **ConfigurationPath** del archivo `web.config` del servidor de extracción (normalmente `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="15930-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="15930-148">Nomenclatura de los documentos de configuración en el servidor de extracción en PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="15930-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="15930-149">Si extrae una sola configuración parcial de un servidor de extracción individual, el documento de configuración puede tener cualquier nombre.</span><span class="sxs-lookup"><span data-stu-id="15930-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="15930-150">Si está extrayendo los más de una configuración parcial de un servidor de extracción, el documento de configuración podría denominarse `<ConfigurationName>.mof`, donde *ConfigurationName* es el nombre de la configuración parcial, o `<ConfigurationName>.<NodeName>.mof`, donde *ConfigurationName* es el nombre de la configuración parcial y *NodeName* es el nombre del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="15930-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="15930-151">Esto le permite extraer las configuraciones del servidor de extracción de DSC de Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="15930-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="15930-152">Nomenclatura de los documentos de configuración en el servidor de extracción en PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="15930-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="15930-153">Los documentos de configuración deben nombrarse del modo siguiente: `ConfigurationName.mof`, donde *ConfigurationName* es el nombre de la configuración parcial.</span><span class="sxs-lookup"><span data-stu-id="15930-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="15930-154">En el ejemplo, los documentos de configuración deben nombrarse del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="15930-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="15930-155">Nomenclatura y ubicación de los documentos de configuración en el servidor de extracción (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="15930-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="15930-156">Los documentos de configuración parcial deben ubicarse en la carpeta especificada en el valor **ConfigurationPath** del archivo `web.config` del servidor de extracción (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="15930-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="15930-157">Los documentos de configuración deben tener los nombres siguientes: `<ConfigurationName>.<ConfigurationID>.mof`, donde _ConfigurationName_ es el nombre de la configuración parcial y _ConfigurationID_ es el identificador de configuración definido en el LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="15930-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="15930-158">En el ejemplo, los documentos de configuración deben nombrarse del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="15930-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="15930-159">Ejecución de configuraciones parciales de un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="15930-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="15930-160">Cuando se haya configurado el LCM en el nodo de destino y se hayan creado los documentos de configuración con los nombres correctos en el servidor de extracción, el nodo de destino extraerá las configuraciones parciales, las combinará y aplicará la configuración resultante a intervalos regulares, según especifique la propiedad **RefreshFrequencyMins** del LCM.</span><span class="sxs-lookup"><span data-stu-id="15930-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="15930-161">Si quiere forzar una actualización, puede llamar al cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) para extraer las configuraciones y luego a `Start-DSCConfiguration –UseExisting` para aplicarlas.</span><span class="sxs-lookup"><span data-stu-id="15930-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="15930-162">Configuraciones parciales en los modos de inserción y extracción mixtos</span><span class="sxs-lookup"><span data-stu-id="15930-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="15930-163">También puede mezclar los modos de inserción y extracción para las configuraciones parciales.</span><span class="sxs-lookup"><span data-stu-id="15930-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="15930-164">Es decir, podría tener una configuración parcial que se haya extraído de un servidor de extracción, mientras que otra configuración parcial se inserta.</span><span class="sxs-lookup"><span data-stu-id="15930-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="15930-165">Especifique el modo de actualización de cada configuración parcial, tal como se describe en las secciones anteriores.</span><span class="sxs-lookup"><span data-stu-id="15930-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="15930-166">Por ejemplo, la metaconfiguración siguiente describe el mismo ejemplo, con la configuración parcial de la cuenta de `ServiceAccountConfig` en el modo de extracción y la configuración parcial de `SharePointConfig` en el modo de inserción.</span><span class="sxs-lookup"><span data-stu-id="15930-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="15930-167">Modos de inserción y extracción mixtos mediante ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="15930-167">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="15930-168">Modos de inserción y extracción mixtos mediante ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="15930-168">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="15930-169">Tenga en cuenta que el valor de **RefreshMode** especificado en el bloque Settings es "Pull", pero el valor de **RefreshMode** para configuración parcial de `SharePointConfig` es "Push".</span><span class="sxs-lookup"><span data-stu-id="15930-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="15930-170">Asigne un nombre y localice los archivos MOF de configuración tal y como se ha descrito anteriormente para sus modos de actualización correspondientes.</span><span class="sxs-lookup"><span data-stu-id="15930-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="15930-171">Llame a `Publish-DSCConfiguration` para publicar la configuración parcial de `SharePointConfig` y, o bien espere a que se extraiga la configuración `ServiceAccountConfig` del servidor de incorporación de cambios, o bien fuerce una actualización mediante una llamada a [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="15930-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="15930-172">Configuración parcial de ServiceAccountConfig de ejemplo</span><span class="sxs-lookup"><span data-stu-id="15930-172">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="15930-173">Configuración parcial de SharePointConfig de ejemplo</span><span class="sxs-lookup"><span data-stu-id="15930-173">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="15930-174">Véase también</span><span class="sxs-lookup"><span data-stu-id="15930-174">See Also</span></span>

[<span data-ttu-id="15930-175">Servicio de extracción de Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="15930-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="15930-176">Configuración del administrador de configuración local de Windows</span><span class="sxs-lookup"><span data-stu-id="15930-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)