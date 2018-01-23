---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuración de un cliente de extracción mediante id. de configuración"
ms.openlocfilehash: 6e3dda1de0bfbf52fb876fdcd2dd2e99da4583dd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="75795-103">Configuración de un cliente de extracción mediante id. de configuración</span><span class="sxs-lookup"><span data-stu-id="75795-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="75795-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="75795-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="75795-105">Es necesario indicar a cada nodo de destino que debe usar el modo de extracción y se le debe facilitar la dirección URL donde puede establecer contacto con el servidor de extracción para obtener las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="75795-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="75795-106">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="75795-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="75795-107">Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="75795-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="75795-108">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="75795-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="75795-109">**Nota**: Este tema se aplica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="75795-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="75795-110">Para obtener información sobre cómo configurar un cliente de incorporación de cambios en PowerShell 4.0, consulte [Configuración de un cliente de incorporación de cambios con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="75795-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="75795-111">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="75795-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="75795-112">En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="75795-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="75795-113">El elemento **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="75795-113">The **ServerURL**</span></span>

<span data-ttu-id="75795-114">Después de que se ejecute este script, se crea una nueva carpeta de salida denominada **PullClientConfigID** y se coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="75795-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="75795-115">En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="75795-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="75795-116">Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="75795-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="75795-117">Por ejemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="75795-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="75795-118">Id. de configuración</span><span class="sxs-lookup"><span data-stu-id="75795-118">Configuration ID</span></span>

<span data-ttu-id="75795-119">El script establece la propiedad **ConfigurationID** del LCM en un GUID que se había creado anteriormente para este fin (puede crear un GUID mediante el cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="75795-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="75795-120">La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="75795-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="75795-121">El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse _ConfigurationID_.mof, donde _ConfigurationID_ es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="75795-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="75795-122">Servidor de extracción SMB</span><span class="sxs-lookup"><span data-stu-id="75795-122">SMB pull server</span></span>

<span data-ttu-id="75795-123">Para configurar un cliente que extraiga configuraciones de un servidor SMB, use un bloque **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="75795-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="75795-124">En un bloque **ConfigurationRepositoryShare**, especifique la ruta de acceso al servidor mediante el establecimiento de la propiedad **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="75795-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="75795-125">La metaconfiguración siguiente configura el nodo de destino para que se extraiga de un servidor de incorporación de cambios SMB denominado **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="75795-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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

## <a name="resource-and-report-servers"></a><span data-ttu-id="75795-126">Servidores de informes y recursos</span><span class="sxs-lookup"><span data-stu-id="75795-126">Resource and report servers</span></span>

<span data-ttu-id="75795-127">Si solo especifica un bloque **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** en la configuración del LCM (como en el ejemplo anterior), el cliente de extracción extraerá recursos del servidor especificado, pero no le enviará informes.</span><span class="sxs-lookup"><span data-stu-id="75795-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="75795-128">Puede usar un solo servidor de extracción para configuraciones, recursos e informes, pero debe crear un bloque **ReportRepositoryWeb** para configurar los informes.</span><span class="sxs-lookup"><span data-stu-id="75795-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="75795-129">En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="75795-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="75795-130">También puede especificar servidores de incorporación de cambios diferentes para los recursos y los informes.</span><span class="sxs-lookup"><span data-stu-id="75795-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="75795-131">Para especificar un servidor de recursos, utilice un bloque **ResourceRepositoryWeb** (para un servidor de extracción web) o un bloque **ResourceRepositoryShare** (para un servidor de extracción SMB).</span><span class="sxs-lookup"><span data-stu-id="75795-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="75795-132">Para especificar un servidor de informes, utilice un bloque **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="75795-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="75795-133">Un servidor de informes no puede ser un servidor SMB.</span><span class="sxs-lookup"><span data-stu-id="75795-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="75795-134">La metaconfiguración siguiente configura un cliente de extracción para que obtenga sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**, y para que envíe los informes a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="75795-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75795-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="75795-135">See Also</span></span>

* [<span data-ttu-id="75795-136">Configuración de un cliente de extracción con nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="75795-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

