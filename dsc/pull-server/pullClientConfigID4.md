---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurar un cliente de incorporación de cambios con identificadores de configuración de PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402993"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="9709b-103">Configurar un cliente de incorporación de cambios con identificadores de configuración de PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="9709b-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="9709b-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9709b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9709b-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="9709b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="9709b-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="9709b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="9709b-107">Antes de configurar un cliente de extracción, debe configurar un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="9709b-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="9709b-108">Aunque este orden no es necesario, ayuda a solucionar problemas y le ayuda a asegurarse de que el registro fue correcto.</span><span class="sxs-lookup"><span data-stu-id="9709b-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="9709b-109">Para configurar un servidor de extracción, puede usar a las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="9709b-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="9709b-110">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="9709b-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9709b-111">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="9709b-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="9709b-112">Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado.</span><span class="sxs-lookup"><span data-stu-id="9709b-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="9709b-113">Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido de SMB o el servidor de extracción de DSC de HTTP.</span><span class="sxs-lookup"><span data-stu-id="9709b-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="9709b-114">Cuando se actualiza el LCM del nodo, se comunicará a la ubicación configurada para descargar las configuraciones asignadas.</span><span class="sxs-lookup"><span data-stu-id="9709b-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="9709b-115">Si todos los recursos necesarios no existen en el nodo, se descargarán automáticamente ellos desde la ubicación configurada.</span><span class="sxs-lookup"><span data-stu-id="9709b-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="9709b-116">Si el nodo se configura con un [servidor de informes](reportServer.md), a continuación, notificará el estado de la operación.</span><span class="sxs-lookup"><span data-stu-id="9709b-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="9709b-117">Configurar el LCM de cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="9709b-117">Configure the pull client LCM</span></span>

<span data-ttu-id="9709b-118">Ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigID** y coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="9709b-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="9709b-119">En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="9709b-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="9709b-120">Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="9709b-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="9709b-121">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9709b-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="9709b-122">Id. de configuración</span><span class="sxs-lookup"><span data-stu-id="9709b-122">Configuration ID</span></span>

<span data-ttu-id="9709b-123">Los ejemplos siguientes conjunto el **ConfigurationID** propiedades del LCM en un **Guid** que había creado anteriormente para este propósito.</span><span class="sxs-lookup"><span data-stu-id="9709b-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="9709b-124">La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="9709b-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="9709b-125">El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="9709b-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="9709b-126">Para obtener más información, consulte [publicar las configuraciones a un servidor de extracción (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="9709b-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="9709b-127">Puede crear uno aleatorio **Guid** mediante el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="9709b-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="9709b-128">Configurar un cliente de extracción para descargar las configuraciones</span><span class="sxs-lookup"><span data-stu-id="9709b-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="9709b-129">Cada cliente debe configurarse en **extracción** modo y dada la incorporación de cambios de dirección url del servidor donde se almacena su configuración.</span><span class="sxs-lookup"><span data-stu-id="9709b-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="9709b-130">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="9709b-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="9709b-131">Para configurar el LCM, debe crear un tipo especial de configuración, con un **LocalConfigurationManager** bloque.</span><span class="sxs-lookup"><span data-stu-id="9709b-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="9709b-132">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="9709b-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="9709b-133">Servidor de extracción de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="9709b-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="9709b-134">Si el servidor de extracción está configurado como un servicio web, establezca el **DownloadManagerName** a **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="9709b-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="9709b-135">El **WebDownloadManager** requiere que especifique un **ServerUrl** a la **DownloadManagerCustomData** clave.</span><span class="sxs-lookup"><span data-stu-id="9709b-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="9709b-136">También puede especificar un valor para **AllowUnsecureConnection**, como en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="9709b-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="9709b-137">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "PullServer".</span><span class="sxs-lookup"><span data-stu-id="9709b-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="9709b-138">Recurso compartido de SMB</span><span class="sxs-lookup"><span data-stu-id="9709b-138">SMB Share</span></span>

<span data-ttu-id="9709b-139">Si el servidor de extracción está configurado como un recurso compartido de archivos SMB, en lugar de un servicio web, establezca el **DownloadManagerName** a **DscFileDownloadManager** en lugar de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="9709b-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="9709b-140">El **DscFileDownloadManager** requiere que especifique un **SourcePath** propiedad en el **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="9709b-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="9709b-141">El script siguiente configura LCM para que extraiga las configuraciones de un recurso compartido SMB denominado "SmbDscShare" en un servidor denominado "CONTOSO-SERVER".</span><span class="sxs-lookup"><span data-stu-id="9709b-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="9709b-142">Pasos a seguir</span><span class="sxs-lookup"><span data-stu-id="9709b-142">Next Steps</span></span>

<span data-ttu-id="9709b-143">Una vez que se ha configurado el cliente de extracción, puede usar a las siguientes guías para realizar los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="9709b-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="9709b-144">Publicación de las configuraciones en un servidor de extracción (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="9709b-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="9709b-145">Empaquetado y carga de recursos en un servidor de extracción (v4)</span><span class="sxs-lookup"><span data-stu-id="9709b-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="9709b-146">Véase también</span><span class="sxs-lookup"><span data-stu-id="9709b-146">See Also</span></span>

- [<span data-ttu-id="9709b-147">Configurar un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="9709b-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="9709b-148">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="9709b-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
