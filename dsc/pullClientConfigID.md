---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción mediante id. de configuración
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="07206-103">Configuración de un cliente de extracción mediante id. de configuración</span><span class="sxs-lookup"><span data-stu-id="07206-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="07206-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="07206-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07206-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="07206-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="07206-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="07206-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="07206-107">Es necesario indicar a cada nodo de destino que debe usar el modo de extracción y se le debe facilitar la dirección URL donde puede establecer contacto con el servidor de extracción para obtener las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="07206-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="07206-108">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="07206-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="07206-109">Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="07206-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="07206-110">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="07206-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="07206-111">**Nota**: Este tema se aplica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="07206-111">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="07206-112">Para obtener información sobre cómo configurar un cliente de incorporación de cambios en PowerShell 4.0, consulte [Configuración de un cliente de incorporación de cambios con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="07206-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="07206-113">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="07206-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="07206-114">En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="07206-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="07206-115">El elemento **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="07206-115">The **ServerURL**</span></span>

<span data-ttu-id="07206-116">Después de que se ejecute este script, se crea una nueva carpeta de salida denominada **PullClientConfigID** y se coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="07206-116">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="07206-117">En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="07206-117">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="07206-118">Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="07206-118">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="07206-119">Por ejemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="07206-119">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="07206-120">Id. de configuración</span><span class="sxs-lookup"><span data-stu-id="07206-120">Configuration ID</span></span>

<span data-ttu-id="07206-121">El script establece la propiedad **ConfigurationID** del LCM en un GUID que se había creado anteriormente para este fin (puede crear un GUID mediante el cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="07206-121">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="07206-122">La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="07206-122">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="07206-123">El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse _ConfigurationID_.mof, donde _ConfigurationID_ es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="07206-123">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="07206-124">Servidor de extracción SMB</span><span class="sxs-lookup"><span data-stu-id="07206-124">SMB pull server</span></span>

<span data-ttu-id="07206-125">Para configurar un cliente que extraiga configuraciones de un servidor SMB, use un bloque **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="07206-125">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="07206-126">En un bloque **ConfigurationRepositoryShare**, especifique la ruta de acceso al servidor mediante el establecimiento de la propiedad **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="07206-126">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="07206-127">La metaconfiguración siguiente configura el nodo de destino para que se extraiga de un servidor de incorporación de cambios SMB denominado **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="07206-127">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="07206-128">Servidores de informes y recursos</span><span class="sxs-lookup"><span data-stu-id="07206-128">Resource and report servers</span></span>

<span data-ttu-id="07206-129">Si solo especifica un bloque **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** en la configuración del LCM (como en el ejemplo anterior), el cliente de extracción extraerá recursos del servidor especificado, pero no le enviará informes.</span><span class="sxs-lookup"><span data-stu-id="07206-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="07206-130">Puede usar un solo servidor de extracción para configuraciones, recursos e informes, pero debe crear un bloque **ReportRepositoryWeb** para configurar los informes.</span><span class="sxs-lookup"><span data-stu-id="07206-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="07206-131">En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="07206-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="07206-132">También puede especificar servidores de incorporación de cambios diferentes para los recursos y los informes.</span><span class="sxs-lookup"><span data-stu-id="07206-132">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="07206-133">Para especificar un servidor de recursos, utilice un bloque **ResourceRepositoryWeb** (para un servidor de extracción web) o un bloque **ResourceRepositoryShare** (para un servidor de extracción SMB).</span><span class="sxs-lookup"><span data-stu-id="07206-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="07206-134">Para especificar un servidor de informes, utilice un bloque **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="07206-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="07206-135">Un servidor de informes no puede ser un servidor SMB.</span><span class="sxs-lookup"><span data-stu-id="07206-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="07206-136">La metaconfiguración siguiente configura un cliente de extracción para que obtenga sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**, y para que envíe los informes a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="07206-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a><span data-ttu-id="07206-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="07206-137">See Also</span></span>

* [<span data-ttu-id="07206-138">Configuración de un cliente de extracción con nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="07206-138">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)