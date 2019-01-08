---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurar un cliente de extracción mediante nombres de configuración en PowerShell 5.0 y versiones posteriores
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403033"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="b88c0-103">Configurar un cliente de extracción mediante nombres de configuración en PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="b88c0-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="b88c0-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b88c0-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b88c0-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b88c0-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b88c0-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b88c0-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b88c0-107">Antes de configurar un cliente de extracción, debe configurar un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="b88c0-108">Aunque este orden no es necesario, ayuda a solucionar problemas y le ayuda a asegurarse de que el registro fue correcto.</span><span class="sxs-lookup"><span data-stu-id="b88c0-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="b88c0-109">Para configurar un servidor de extracción, puede usar a las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="b88c0-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="b88c0-110">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="b88c0-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b88c0-111">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="b88c0-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b88c0-112">Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado.</span><span class="sxs-lookup"><span data-stu-id="b88c0-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b88c0-113">Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido de SMB o el servidor de extracción de DSC de HTTP.</span><span class="sxs-lookup"><span data-stu-id="b88c0-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="b88c0-114">Cuando se actualiza el LCM del nodo, se comunicará a la ubicación configurada para descargar las configuraciones asignadas.</span><span class="sxs-lookup"><span data-stu-id="b88c0-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="b88c0-115">Si todos los recursos necesarios no existen en el nodo, se descargarán automáticamente ellos desde la ubicación configurada.</span><span class="sxs-lookup"><span data-stu-id="b88c0-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="b88c0-116">Si el nodo se configura con un [servidor de informes](reportServer.md), a continuación, notificará el estado de la operación.</span><span class="sxs-lookup"><span data-stu-id="b88c0-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="b88c0-117">**Nota**: En este tema se aplica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b88c0-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="b88c0-118">Para obtener información acerca de cómo configurar un cliente de extracción en PowerShell 4.0, consulte [configurar un cliente de extracción mediante Id. de configuración en PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="b88c0-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="b88c0-119">Configurar el LCM de cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="b88c0-119">Configure the pull client LCM</span></span>

<span data-ttu-id="b88c0-120">Ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigName** y coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="b88c0-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="b88c0-121">En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="b88c0-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="b88c0-122">Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="b88c0-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="b88c0-123">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="b88c0-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="b88c0-124">Nombre de la configuración</span><span class="sxs-lookup"><span data-stu-id="b88c0-124">Configuration Name</span></span>

<span data-ttu-id="b88c0-125">Los ejemplos siguientes se establece la **ConfigurationName** propiedades del LCM en el nombre de una configuración previamente compilado, creado para este propósito.</span><span class="sxs-lookup"><span data-stu-id="b88c0-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="b88c0-126">El **ConfigurationName** es lo que usa el LCM para buscar la configuración adecuada en el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="b88c0-127">El archivo MOF de configuración en el servidor de incorporación de cambios debe denominarse `<ConfigurationName>.mof`, en este caso, "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="b88c0-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="b88c0-128">Para obtener más información, consulte [publicar las configuraciones a un servidor de extracción (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="b88c0-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="b88c0-129">Configurar un cliente de extracción para descargar las configuraciones</span><span class="sxs-lookup"><span data-stu-id="b88c0-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="b88c0-130">Cada cliente debe configurarse en **extracción** modo y dada la incorporación de cambios de dirección url del servidor donde se almacena su configuración.</span><span class="sxs-lookup"><span data-stu-id="b88c0-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="b88c0-131">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="b88c0-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="b88c0-132">Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="b88c0-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="b88c0-133">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="b88c0-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="b88c0-134">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="b88c0-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="b88c0-135">En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="b88c0-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="b88c0-136">La propiedad **ServerURL** especifica el punto de conexión del servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="b88c0-137">La propiedad **RegistrationKey** es una clave compartida entre todos los nodos de cliente de un servidor de extracción y ese servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="b88c0-138">El mismo valor se almacena en un archivo en el servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="b88c0-139">**Nota**: Las claves de registro solo funcionan con **web** servidores de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="b88c0-140">Deberá seguir usando el elemento **ConfigurationID** con un servidor de extracción **SMB**.</span><span class="sxs-lookup"><span data-stu-id="b88c0-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="b88c0-141">Para obtener información sobre cómo configurar un servidor de extracción mediante **ConfigurationID**, consulte [Configuración de un cliente de extracción con el id. de configuración](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="b88c0-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="b88c0-142">La propiedad **ConfigurationNames** es una matriz que especifica el nombre de la configuración prevista para el nodo de cliente.</span><span class="sxs-lookup"><span data-stu-id="b88c0-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="b88c0-143">**Nota:** Si se especifica más de un valor en **ConfigurationNames**, también deberá especificar bloques **PartialConfiguration** en la configuración.</span><span class="sxs-lookup"><span data-stu-id="b88c0-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="b88c0-144">Para obtener información sobre las configuraciones parciales, consulte [Configuraciones parciales de la configuración de estado deseado de PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="b88c0-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="b88c0-145">Configurar un cliente de extracción para descargar los recursos</span><span class="sxs-lookup"><span data-stu-id="b88c0-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="b88c0-146">Si solo especifica un **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** bloquear en su configuración del LCM (como se muestra en el ejemplo anterior), el cliente de extracción extraerá recursos del mismo ubicación donde se almacenan los archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="b88c0-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="b88c0-147">También puede especificar distintas ubicaciones donde los clientes puedan descargar los recursos.</span><span class="sxs-lookup"><span data-stu-id="b88c0-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="b88c0-148">Para especificar un servidor de recursos, utilice un bloque **ResourceRepositoryWeb** (para un servidor de extracción web) o un bloque **ResourceRepositoryShare** (para un servidor de extracción SMB).</span><span class="sxs-lookup"><span data-stu-id="b88c0-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="b88c0-149">El ejemplo siguiente muestra una metaconfiguration que configura un cliente para descargar las configuraciones de un servidor de extracción y recursos desde un recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="b88c0-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="b88c0-150">Configurar un cliente de incorporación de cambios para informar del estado</span><span class="sxs-lookup"><span data-stu-id="b88c0-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="b88c0-151">Puede usar un único servidor de extracción para configuraciones, recursos e informes.</span><span class="sxs-lookup"><span data-stu-id="b88c0-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="b88c0-152">Informes no están configurados para los clientes de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="b88c0-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="b88c0-153">Para configurar un cliente para informar del estado, tendrá que crear un **ReportRepositoryWeb** bloque.</span><span class="sxs-lookup"><span data-stu-id="b88c0-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="b88c0-154">En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="b88c0-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="b88c0-155">Un servidor de informes no puede ser un recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="b88c0-155">A report server cannot be an SMB share.</span></span>

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="b88c0-156">Véase también</span><span class="sxs-lookup"><span data-stu-id="b88c0-156">See Also</span></span>

* [<span data-ttu-id="b88c0-157">Configuración de un cliente de extracción con el id. de configuración</span><span class="sxs-lookup"><span data-stu-id="b88c0-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="b88c0-158">Configuración de un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="b88c0-158">Setting up a DSC web pull server</span></span>](pullServer.md)
