---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción mediante nombres de configuración
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="4ff1a-103">Configuración de un cliente de extracción mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="4ff1a-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="4ff1a-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4ff1a-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ff1a-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="4ff1a-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="4ff1a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="4ff1a-107">Es necesario indicar a cada nodo de destino que debe usar el modo de extracción y se le debe facilitar la dirección URL donde puede establecer contacto con el servidor de extracción para obtener las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="4ff1a-108">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="4ff1a-109">Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="4ff1a-110">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="4ff1a-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="4ff1a-111">**Nota**: Este tema se aplica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-111">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="4ff1a-112">Para obtener información sobre cómo configurar un cliente de extracción en PowerShell 4.0, consulte [Configuración de un cliente de extracción con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="4ff1a-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="4ff1a-113">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv":</span><span class="sxs-lookup"><span data-stu-id="4ff1a-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="4ff1a-114">En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="4ff1a-115">La propiedad **ServerURL** especifica el punto de conexión del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-115">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="4ff1a-116">La propiedad **RegistrationKey** es una clave compartida entre todos los nodos de cliente de un servidor de extracción y ese servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-116">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="4ff1a-117">El mismo valor se almacena en un archivo en el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-117">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="4ff1a-118">La propiedad **ConfigurationNames** es una matriz que especifica el nombre de la configuración prevista para el nodo de cliente.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-118">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="4ff1a-119">En el servidor de extracción, el archivo MOF de configuración de este nodo de cliente debe denominarse *ConfigurationNames*.mof, donde *ConfigurationNames* coincide con el valor de la propiedad **ConfigurationNames** establecida en este metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-119">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="4ff1a-120">**Nota**: Si se especifica más de un valor en **ConfigurationNames**, también debe especificar bloques **PartialConfiguration** en la configuración.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-120">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="4ff1a-121">Para obtener información sobre las configuraciones parciales, consulte [Configuraciones parciales de la configuración de estado deseado de PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="4ff1a-121">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="4ff1a-122">Después de que se ejecute este script, se crea una nueva carpeta de salida denominada **PullClientConfigNames** y se coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-122">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="4ff1a-123">En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-123">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="4ff1a-124">Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-124">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="4ff1a-125">**Nota**: Las claves de registro solo funcionan con servidores de extracción web.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-125">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="4ff1a-126">Deberá seguir usando el elemento **ConfigurationID** con un servidor de extracción SMB.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-126">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="4ff1a-127">Para obtener información sobre cómo configurar un servidor de extracción mediante **ConfigurationID**, consulte [Configuración de un cliente de extracción con el id. de configuración](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="4ff1a-127">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="4ff1a-128">Servidores de informes y recursos</span><span class="sxs-lookup"><span data-stu-id="4ff1a-128">Resource and report servers</span></span>

<span data-ttu-id="4ff1a-129">Si solo especifica un bloque **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** en la configuración del LCM (como en el ejemplo anterior), el cliente de extracción extraerá recursos del servidor especificado, pero no le enviará informes.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="4ff1a-130">Puede usar un solo servidor de extracción para configuraciones, recursos e informes, pero debe crear un bloque **ReportRepositoryWeb** para configurar los informes.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="4ff1a-131">En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="4ff1a-132">También puede especificar servidores de incorporación de cambios diferentes para los recursos y los informes.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-132">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="4ff1a-133">Para especificar un servidor de recursos, utilice un bloque **ResourceRepositoryWeb** (para un servidor de extracción web) o un bloque **ResourceRepositoryShare** (para un servidor de extracción SMB).</span><span class="sxs-lookup"><span data-stu-id="4ff1a-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="4ff1a-134">Para especificar un servidor de informes, utilice un bloque **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="4ff1a-135">Un servidor de informes no puede ser un servidor SMB.</span><span class="sxs-lookup"><span data-stu-id="4ff1a-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="4ff1a-136">La metaconfiguración siguiente configura un cliente de extracción para que obtenga sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**, y para que envíe los informes a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="4ff1a-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="4ff1a-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="4ff1a-137">See Also</span></span>

* [<span data-ttu-id="4ff1a-138">Configuración de un cliente de extracción con el id. de configuración</span><span class="sxs-lookup"><span data-stu-id="4ff1a-138">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="4ff1a-139">Configuración de un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="4ff1a-139">Setting up a DSC web pull server</span></span>](pullServer.md)