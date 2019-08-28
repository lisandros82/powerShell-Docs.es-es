---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de un servidor de informes de DSC
ms.openlocfilehash: 1ccd4f96b782b41b7d7c953735cb41b3ba3d2bce
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986559"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="5df9f-103">Uso de un servidor de informes de DSC</span><span class="sxs-lookup"><span data-stu-id="5df9f-103">Using a DSC report server</span></span>

<span data-ttu-id="5df9f-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5df9f-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5df9f-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="5df9f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="5df9f-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="5df9f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="5df9f-107">El servidor de informes que se describe en este tema no está disponible en PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="5df9f-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="5df9f-108">El administrador de configuración local (LCM) de un nodo se puede configurar para enviar informes sobre su estado de configuración a un servidor de extracción, que puede consultarse posteriormente para recuperar los datos.</span><span class="sxs-lookup"><span data-stu-id="5df9f-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="5df9f-109">Cada vez que el nodo comprueba y aplica una configuración, envía un informe al servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="5df9f-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="5df9f-110">Estos informes se almacenan en una base de datos en el servidor y se pueden recuperar mediante una llamada al servicio web de informes.</span><span class="sxs-lookup"><span data-stu-id="5df9f-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="5df9f-111">Cada informe contiene información como qué configuraciones se han aplicado y si lo han hecho correctamente, los recursos usados, los errores que se han producido y las horas de inicio y finalización.</span><span class="sxs-lookup"><span data-stu-id="5df9f-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="5df9f-112">Configuración de un nodo para enviar informes</span><span class="sxs-lookup"><span data-stu-id="5df9f-112">Configuring a node to send reports</span></span>

<span data-ttu-id="5df9f-113">Puede indicar a un nodo que envíe informes a un servidor mediante un bloque **ReportServerWeb** en la configuración del LCM del nodo (para más información sobre cómo configurar el LCM, vea [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md)).</span><span class="sxs-lookup"><span data-stu-id="5df9f-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="5df9f-114">El servidor al que el nodo envía los informes debe estar configurado como un servidor de extracción web (no puede enviar informes a un recurso compartido SMB).</span><span class="sxs-lookup"><span data-stu-id="5df9f-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="5df9f-115">Para obtener información sobre la configuración de un servidor de extracción, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="5df9f-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="5df9f-116">El servidor de informes puede ser el mismo servicio desde el que el nodo extrae configuraciones y obtiene recursos, o puede ser un servicio diferente.</span><span class="sxs-lookup"><span data-stu-id="5df9f-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="5df9f-117">En el bloque **ReportServerWeb**, debe especificar la dirección URL del servicio de extracción y una clave de registro que sea conocida para el servidor.</span><span class="sxs-lookup"><span data-stu-id="5df9f-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="5df9f-118">La configuración siguiente configura un nodo para que extraiga configuraciones de un servicio y envíe informes a un servicio en un servidor diferente.</span><span class="sxs-lookup"><span data-stu-id="5df9f-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="5df9f-119">La configuración siguiente define un nodo para que utilice un único servidor para las configuraciones, los recursos y los informes.</span><span class="sxs-lookup"><span data-stu-id="5df9f-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
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



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="5df9f-120">Puede asignar el nombre que quiera al servicio web al configurar un servidor de incorporación de cambios, pero la propiedad **ServerURL** debe coincidir con el nombre del servicio.</span><span class="sxs-lookup"><span data-stu-id="5df9f-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="5df9f-121">Obtener datos de informes</span><span class="sxs-lookup"><span data-stu-id="5df9f-121">Getting report data</span></span>

<span data-ttu-id="5df9f-122">Los informes enviados al servidor de extracción se introducen en una base de datos del servidor.</span><span class="sxs-lookup"><span data-stu-id="5df9f-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="5df9f-123">Los informes están disponibles a través de llamadas al servicio web.</span><span class="sxs-lookup"><span data-stu-id="5df9f-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="5df9f-124">Para recuperar informes para un nodo específico, envíe una solicitud HTTP al servicio web de informes de la forma siguiente: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="5df9f-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="5df9f-125">donde `MyNodeAgentId` es el valor AgentId del nodo para el que desea obtener informes.</span><span class="sxs-lookup"><span data-stu-id="5df9f-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="5df9f-126">Puede obtener el valor de AgentId de un nodo mediante una llamada a [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) en ese nodo.</span><span class="sxs-lookup"><span data-stu-id="5df9f-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="5df9f-127">Los informes se devuelven como una matriz de objetos JSON.</span><span class="sxs-lookup"><span data-stu-id="5df9f-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="5df9f-128">El script siguiente devuelve los informes para el nodo en el que se ejecuta:</span><span class="sxs-lookup"><span data-stu-id="5df9f-128">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="5df9f-129">Visualización de los datos de los informes</span><span class="sxs-lookup"><span data-stu-id="5df9f-129">Viewing report data</span></span>

<span data-ttu-id="5df9f-130">Si establece una variable como el resultado de la función **GetReport**, puede ver los campos individuales de un elemento de la matriz que se devuelve:</span><span class="sxs-lookup"><span data-stu-id="5df9f-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="5df9f-131">De forma predeterminada, los informes se ordenan por **JobID**.</span><span class="sxs-lookup"><span data-stu-id="5df9f-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="5df9f-132">Para obtener el informe más reciente, los informes se pueden ordenar en orden descendente por la propiedad **StartTime** y, luego, obtener el primer elemento de la matriz:</span><span class="sxs-lookup"><span data-stu-id="5df9f-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="5df9f-133">Observe que la propiedad **StatusData** es un objeto con varias propiedades.</span><span class="sxs-lookup"><span data-stu-id="5df9f-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="5df9f-134">En esto consisten en gran medida los datos de informes.</span><span class="sxs-lookup"><span data-stu-id="5df9f-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="5df9f-135">Echemos un vistazo a los campos individuales de la propiedad **StatusData** del informe más reciente:</span><span class="sxs-lookup"><span data-stu-id="5df9f-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="5df9f-136">Entre otras cosas, muestra que la configuración más reciente llamó a dos recursos y que uno de ellos estaba en el estado deseado, pero el otro no.</span><span class="sxs-lookup"><span data-stu-id="5df9f-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="5df9f-137">Puede obtener una salida más legible solo de la propiedad **ResourcesNotInDesiredState**:</span><span class="sxs-lookup"><span data-stu-id="5df9f-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="5df9f-138">Tenga en cuenta que estos ejemplos están diseñados para ofrecerle una idea de lo que puede hacer con los datos del informe.</span><span class="sxs-lookup"><span data-stu-id="5df9f-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="5df9f-139">Para obtener una introducción sobre cómo trabajar con JSON en PowerShell, vea [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/) (Experimentos con JSON y PowerShell).</span><span class="sxs-lookup"><span data-stu-id="5df9f-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="5df9f-140">Véase también</span><span class="sxs-lookup"><span data-stu-id="5df9f-140">See Also</span></span>

[<span data-ttu-id="5df9f-141">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="5df9f-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="5df9f-142">Configuración de un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="5df9f-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="5df9f-143">Configuración de un cliente de extracción mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="5df9f-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
