---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Solución de problemas de DSC"
ms.openlocfilehash: 9b1266b9c8923474005760ef78b05d570efdde37
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="6ac1f-103">Solución de problemas de DSC</span><span class="sxs-lookup"><span data-stu-id="6ac1f-103">Troubleshooting DSC</span></span>

><span data-ttu-id="6ac1f-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6ac1f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6ac1f-105">Este tema describen las distintas formas de solucionar problemas de DSC cuando surgen.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="6ac1f-106">Dependencia de WinRM</span><span class="sxs-lookup"><span data-stu-id="6ac1f-106">WinRM Dependency</span></span>

<span data-ttu-id="6ac1f-107">La configuración de estado deseado (DSC) de Windows PowerShell depende de WinRM.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="6ac1f-108">WinRM no está habilitado de forma predeterminada en Windows Server 2008 R2 y Windows 7.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="6ac1f-109">Para habilitar WinRM, ejecute ```Set-WSManQuickConfig``` en una sesión de Windows PowerShell con permisos elevados.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-109">Run ```Set-WSManQuickConfig```, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="6ac1f-110">Uso de Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6ac1f-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="6ac1f-111">El cmdlet [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx) obtiene información acerca del estado de la configuración de un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="6ac1f-112">Se devuelve un objeto enriquecido que incluye información detallada sobre si la configuración de ejecución era correcta o no.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="6ac1f-113">Ya puede adentrarse en el objeto para descubrir los detalles sobre la configuración de ejecución como:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-113">You can dig into the object to discover details about the configuration run such as:</span></span>

* <span data-ttu-id="6ac1f-114">Todos los recursos con errores.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-114">All of the resources that failed</span></span>
* <span data-ttu-id="6ac1f-115">Cualquier recurso que solicitó un reinicio.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-115">Any resource that requested a reboot</span></span>
* <span data-ttu-id="6ac1f-116">Las opciones de metaconfiguración en tiempo de ejecución de la configuración.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-116">Meta-Configuration settings at time of configuration run</span></span>
* <span data-ttu-id="6ac1f-117">Etc.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-117">Etc.</span></span>

<span data-ttu-id="6ac1f-118">El siguiente conjunto de parámetros devuelve la información de estado de la última ejecución de la configuración:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-118">The following parameter set returns the status information for the last configuration run:</span></span>

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
<span data-ttu-id="6ac1f-119">El siguiente conjunto de parámetros devuelve la información de estado de todas las ejecuciones anteriores de la configuración:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="6ac1f-120">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6ac1f-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="6ac1f-121">El script no se ejecuta: uso de registros de DSC para diagnosticar errores de scripts</span><span class="sxs-lookup"><span data-stu-id="6ac1f-121">My script won’t run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="6ac1f-122">Como sucede con todo el software de Windows, DSC registra los errores y eventos en [registros](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) que se pueden ver en el [Visor de eventos](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span> <span data-ttu-id="6ac1f-123">Examinar estos registros puede ayudarle a entender el motivo del error de una operación determinada y cómo evitar los errores en el futuro.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="6ac1f-124">La escritura de scripts de configuración puede ser complicada, por lo que para que sea más fácil realizar un seguimiento de los errores a medida que se crea, utilice el recurso de registro de DSC para hacer un seguimiento del progreso de la configuración en el registro de eventos DSC Analytic.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="6ac1f-125">¿Dónde se encuentran los registros de eventos de DSC?</span><span class="sxs-lookup"><span data-stu-id="6ac1f-125">Where are DSC event logs?</span></span>

<span data-ttu-id="6ac1f-126">En el Visor de eventos, los eventos de DSC se encuentran en: **Registros de aplicaciones y servicios/Microsoft/Windows/Configuración de estado deseado**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="6ac1f-127">El cmdlet de PowerShell correspondiente, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), también se puede ejecutar para ver los registros de eventos:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

<span data-ttu-id="6ac1f-128">Como se muestra arriba, el nombre del registro primario de DSC es **Microsoft->Windows->DSC** (no se muestran otros nombres de registros de Windows por razones de brevedad).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-128">As shown above, DSC’s primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="6ac1f-129">El nombre principal se anexa al nombre del canal para crear el nombre del registro completo.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="6ac1f-130">El motor de DSC escribe principalmente en tres tipos de registros: [registros operativos, analíticos y de depuración](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="6ac1f-131">Como los registros analíticos y de depuración están desactivados de forma predeterminada, debe habilitarlos en el Visor de eventos.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="6ac1f-132">Para ello, abra el Visor de eventos escribiendo Show-EventLog en Windows PowerShell, o bien, haga clic en el botón **Inicio**, **Panel de Control**, **Herramientas administrativas** y luego haga clic en **Visor de eventos**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span> <span data-ttu-id="6ac1f-133">En el menú **Vista** del Visor de eventos, haga clic en **Mostrar registros analíticos y de depuración**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="6ac1f-134">El nombre del registro del canal analítico **Microsoft-Windows-Dsc/Analytic** y el del canal de depuración **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="6ac1f-135">También puede usar la utilidad [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) para habilitar los registros, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="6ac1f-136">¿Qué contienen los registros de DSC?</span><span class="sxs-lookup"><span data-stu-id="6ac1f-136">What do DSC logs contain?</span></span>

<span data-ttu-id="6ac1f-137">Los registros de DSC se dividen en los tres canales de registro según la importancia del mensaje.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="6ac1f-138">El registro operativo de DSC contiene todos los mensajes de error y puede utilizarse para identificar un problema.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="6ac1f-139">El registro analítico tiene un mayor volumen de eventos y puede identificar dónde se han producido errores.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="6ac1f-140">Este canal también contiene los mensajes detallados (si existen).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="6ac1f-141">El registro de depuración contiene registros que pueden ayudarle a entender cómo se produjeron los errores.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="6ac1f-142">Los mensajes de los eventos de DSC se estructuran de forma que cada mensaje de evento comienza por un identificador de trabajo que representa de forma única una operación de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="6ac1f-143">En el ejemplo siguiente intenta obtener el mensaje desde el primer evento registrado en el registro operativo de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

<span data-ttu-id="6ac1f-144">Los eventos de DSC se registran en una estructura determinada que permite al usuario agrupar los eventos de un trabajo de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="6ac1f-145">La estructura es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-145">The structure is as follows:</span></span>

<span data-ttu-id="6ac1f-146">**Id. de trabajo: <Guid>**
**<Event Message>**</span><span class="sxs-lookup"><span data-stu-id="6ac1f-146">**Job ID : <Guid>**
**<Event Message>**</span></span>

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="6ac1f-147">Recopilación de eventos de una operación de DSC única</span><span class="sxs-lookup"><span data-stu-id="6ac1f-147">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="6ac1f-148">Los registros de eventos de DSC contienen los eventos que han generado diferentes operaciones de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-148">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="6ac1f-149">Sin embargo, normalmente solo le interesarán los detalles sobre una operación determinada.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-149">However, you’ll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="6ac1f-150">Todos los registros de DSC se pueden agrupar según la propiedad de identificador de trabajo, que es única para cada operación de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-150">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="6ac1f-151">El identificador de trabajo se muestra como el primer valor de propiedad de todos los eventos de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-151">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="6ac1f-152">En los siguientes pasos se explica cómo acumular todos los eventos en una estructura de matriz agrupada.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-152">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}  
```

<span data-ttu-id="6ac1f-153">Aquí, la variable `$SeparateDscOperations` contiene registros agrupados por los identificadores de trabajo.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-153">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="6ac1f-154">Cada elemento de la matriz de esta variable representa un grupo de eventos que ha registrado otra operación de DSC, lo que permite el acceso a más información sobre los registros.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-154">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

<span data-ttu-id="6ac1f-155">Puede extraer los datos en la variable `$SeparateDscOperations` con [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-155">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="6ac1f-156">A continuación se muestran cinco escenarios en los que podría querer extraer los datos para la solucionar problemas de DSC:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-156">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="6ac1f-157">1: Errores de operaciones</span><span class="sxs-lookup"><span data-stu-id="6ac1f-157">1: Operations failures</span></span>

<span data-ttu-id="6ac1f-158">Todos los eventos tienen [niveles de gravedad](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-158">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="6ac1f-159">Esta información puede usarse para identificar los eventos de error:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-159">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="6ac1f-160">2: Detalles de las operaciones que se ejecutaron en última media hora</span><span class="sxs-lookup"><span data-stu-id="6ac1f-160">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="6ac1f-161">`TimeCreated`, una propiedad de todos los eventos de Windows, indica la hora en que se creó el evento.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-161">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="6ac1f-162">Se puede hacer una comparación de esta propiedad con un objeto de fecha y hora determinado para filtrar todos los eventos:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-162">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="6ac1f-163">3: Mensajes de la operación más reciente</span><span class="sxs-lookup"><span data-stu-id="6ac1f-163">3: Messages from the latest operation</span></span>

<span data-ttu-id="6ac1f-164">La operación más reciente se almacena en el primer índice del grupo de matrices `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-164">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span> <span data-ttu-id="6ac1f-165">Si se consultan los mensajes del grupo del índice 0, se devuelven todos los mensajes para la operación más reciente:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-165">Querying the group’s messages for index 0 returns all messages for the latest operation:</span></span>

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="6ac1f-166">4: Mensajes de error registrados para operaciones con errores recientes</span><span class="sxs-lookup"><span data-stu-id="6ac1f-166">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="6ac1f-167">`$SeparateDscOperations[0].Group` contiene un conjunto de eventos para la operación más reciente.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-167">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="6ac1f-168">Ejecute el cmdlet `Where-Object` para filtrar los eventos según su nombre para mostrar del nivel.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-168">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="6ac1f-169">Los resultados se almacenan en la variable `$myFailedEvent`, que se puede analizar en más profundidad para obtener el mensaje de evento:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-169">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="6ac1f-170">5: Todos los eventos que ha generado un identificador de trabajo determinado.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-170">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="6ac1f-171">`$SeparateDscOperations` es una matriz de grupos, cada uno de los cuales tiene como nombre el identificador de trabajo único.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-171">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="6ac1f-172">Al ejecutar el cmdlet `Where-Object`, puede extraer esos grupos de eventos que tienen un identificador de trabajo determinado:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-172">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="6ac1f-173">Uso de xDscDiagnostics para analizar registros de DSC</span><span class="sxs-lookup"><span data-stu-id="6ac1f-173">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="6ac1f-174">**xDscDiagnostics** es un módulo de PowerShell que consta de varias funciones que pueden ayudar a analizar los errores de DSC en la máquina.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-174">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="6ac1f-175">Estas funciones pueden ayudar a identificar todos los eventos locales de las operaciones de DSC anteriores o los eventos de DSC de los equipos remotos (con credenciales válidas).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-175">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="6ac1f-176">Aquí, el término operación de DSC se utiliza para definir una única ejecución de DSC desde el inicio hasta el final.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-176">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="6ac1f-177">Por ejemplo, `Test-DscConfiguration` sería una operación de DSC independiente.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-177">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="6ac1f-178">De forma similar, todos los demás cmdlets de DSC (como `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) podrían identificarse uno a uno como operaciones de DSC independientes.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-178">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="6ac1f-179">Las funciones se explican en [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-179">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="6ac1f-180">Puede obtener ayuda si ejecuta `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-180">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="6ac1f-181">Obtención de detalles de las operaciones de DSC</span><span class="sxs-lookup"><span data-stu-id="6ac1f-181">Getting details of DSC operations</span></span> 

<span data-ttu-id="6ac1f-182">La función `Get-xDscOperation` permite buscar los resultados de las operaciones de DSC que se ejecutan en uno o varios equipos, y devuelve un objeto que contiene la colección de eventos que ha producido cada operación de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-182">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="6ac1f-183">Por ejemplo, en la salida siguiente, se ejecutaron tres comandos.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-183">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="6ac1f-184">El primero se realizó correctamente y los otros dos no.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-184">The first one passed, and the other two failed.</span></span> <span data-ttu-id="6ac1f-185">Estos resultados se resumen en la salida de `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-185">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents            
------------   ---------- -----------           ------   -----                                 ---------            
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

<span data-ttu-id="6ac1f-186">También puede especificar que solo desea los resultados de las últimas operaciones, para lo que debe usar el parámetro `Newest`:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-186">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents            
------------   ---------- -----------           ------   -----                                 ---------            
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="6ac1f-187">Obtención de detalles de los eventos de DSC</span><span class="sxs-lookup"><span data-stu-id="6ac1f-187">Getting details of DSC events</span></span>

<span data-ttu-id="6ac1f-188">El cmdlet `Trace-xDscOperation` devuelve un objeto que contiene una colección de eventos, sus tipos de eventos y la salida del mensaje generado a partir de una determinada operación de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-188">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="6ac1f-189">Normalmente, cuando encuentre un error en cualquiera de las operaciones con `Get-xDscOperation`, realizará un seguimiento de esa operación para averiguar qué evento provocó el error.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-189">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="6ac1f-190">Utilice el parámetro `SequenceID` para obtener los eventos de una operación específica de un equipo concreto.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-190">Use the  `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span> <span data-ttu-id="6ac1f-191">Por ejemplo, si en `SequenceID` especifica 9, `Trace-xDscOperaion` obtiene el seguimiento de la operación de DSC que era la novena desde la última operación:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-191">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message                                                                                             
------------   ---------    -----------           -------                                                                                             
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.                
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.                                                                         
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer. 
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.                                                            
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...                                                       
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully. 
```

<span data-ttu-id="6ac1f-192">Pase el **GUID** asignado a una operación de DSC concreta (el que ha devuelto el cmdlet `Get-xDscOperation`) para obtener los detalles de los eventos de dicha operación de DSC:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-192">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message                                                                                             
------------   ---------    -----------           -------                                                                                             
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.                
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof                             
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.                                                                         
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.                          
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.                          
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.                                                                 
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer. 
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]                      
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]                      
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]                      
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]                        
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]                        
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure           
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port             
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State            
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]                        
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.                          
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof                             
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.                                                            
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...                                                       
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.                                         
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="6ac1f-193">Tenga en cuenta que, como `Trace-xDscOperation` agrega eventos de los registros analítico, de depuración y operativo, se le pedirá que habilite estos registros como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-193">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="6ac1f-194">Como alternativa, puede recopilar información sobre los eventos si guarda el resultado de `Trace-xDscOperation` en una variable.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-194">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="6ac1f-195">Puede utilizar los comandos siguientes para mostrar todos los eventos de una operación de DSC concreta.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-195">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="6ac1f-196">Esto mostrará los mismos resultados que el cmdlet `Get-WinEvent`, como se muestra en la salida siguiente:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-196">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```powershell
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message                                                                                           
-----------                     -- ---------------- -------                                                                                           
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.     
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.      
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="6ac1f-197">Idealmente, primero deberá utilizar `Get-xDscOperation` para enumerar las últimas configuraciones DSC que se han ejecutado en las máquinas.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-197">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="6ac1f-198">A continuación, puede examinar cualquier operación única (mediante su valor de SequenceID o JobID) con `Trace-xDscOperation` para descubrir lo que hizo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-198">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="6ac1f-199">Obtención de eventos de un equipo remoto</span><span class="sxs-lookup"><span data-stu-id="6ac1f-199">Getting events for a remote computer</span></span>

<span data-ttu-id="6ac1f-200">Utilice el parámetro `ComputerName` del cmdlet `Trace-xDscOperation` para obtener los detalles de los eventos de un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-200">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="6ac1f-201">Para ello, antes es preciso crear una regla de firewall que permita la administración remota en el equipo remoto:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-201">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
<span data-ttu-id="6ac1f-202">A partir de ahí se puede especificar dicho equipo en la llamada a `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-202">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="6ac1f-203">Los recursos no se actualizan: restablecer la memoria caché</span><span class="sxs-lookup"><span data-stu-id="6ac1f-203">My resources won’t update: How to reset the cache</span></span>

<span data-ttu-id="6ac1f-204">El motor de DSC almacena en caché los recursos implementados como un módulo de PowerShell por motivos de eficiencia.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-204">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span> <span data-ttu-id="6ac1f-205">Sin embargo, esto puede provocar problemas cuando está creando un recurso y probándolo al mismo tiempo, ya que DSC cargará la versión en caché hasta que se reinicie el proceso.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-205">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="6ac1f-206">La única manera de conseguir que DSC cargue la versión más reciente es detener explícitamente el proceso que hospeda el motor de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-206">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="6ac1f-207">De forma similar, cuando se ejecuta `Start-DscConfiguration`, después de agregar y modificar un recurso personalizado, es posible que la modificación no se ejecute a menos que (o hasta que) se reinicie el equipo.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-207">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="6ac1f-208">Esto se debe a que DSC se ejecuta en el proceso host del proveedor de WMI (WmiPrvSE) y, normalmente, existen muchas instancias de WmiPrvSE que se ejecutan a la vez.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-208">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="6ac1f-209">Al reiniciar, el proceso de host se reinicia y la memoria caché se borra.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-209">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="6ac1f-210">Para reciclar la configuración de correctamente y borrar la memoria caché sin necesidad de reiniciar, debe detener y después reiniciar el proceso del host.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-210">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="6ac1f-211">Esto puede hacerse por instancia, en cuyo caso se identifica el proceso, se detiene y se reinicia.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-211">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="6ac1f-212">O bien, puede usar `DebugMode`, como se muestra a continuación, para volver a cargar el recurso de DSC de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-212">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="6ac1f-213">Para identificar el proceso que hospeda el motor de DSC y detenerlo por instancia, puede mostrar el identificador de proceso del elemento WmiPrvSE que hospeda el motor de DSC.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-213">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="6ac1f-214">A continuación, para actualizar el proveedor, detenga el proceso WmiPrvSE mediante los comandos siguientes y luego ejecute de nuevo **Start-DscConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-214">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="6ac1f-215">Uso de DebugMode</span><span class="sxs-lookup"><span data-stu-id="6ac1f-215">Using DebugMode</span></span>

<span data-ttu-id="6ac1f-216">Puede configurar el administrador de configuración de local (LCM) de DSC para que utilice `DebugMode` y siempre se borre la memoria caché cuando se reinicie el proceso de host.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-216">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="6ac1f-217">Cuando se establece en **TRUE**, provoca que el motor siempre vuelva a cargar el recurso de DSC de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-217">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="6ac1f-218">Cuando haya terminado de escribir el recurso, se puede volver a establecer en **FALSE** y el motor volverá al comportamiento de almacenamiento en caché de los módulos.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-218">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="6ac1f-219">A continuación se incluye una demostración donde se aprecia cómo `DebugMode` puede actualizar automáticamente la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-219">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="6ac1f-220">En primer lugar, echemos un vistazo a la configuración predeterminada:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-220">First, let’s look at the default configuration:</span></span>

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

<span data-ttu-id="6ac1f-221">Puede ver que `DebugMode` está establecido en **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-221">You can see that `DebugMode` is set to **FALSE**.</span></span>

<span data-ttu-id="6ac1f-222">Para configurar la demostración de `DebugMode`, utilice el siguiente recurso de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-222">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

<span data-ttu-id="6ac1f-223">Ahora, cree una configuración con el recurso anterior denominado `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-223">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="6ac1f-224">Verá que el contenido del archivo "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" es **1**.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-224">You will see that the contents of file: “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” is **1**.</span></span>

<span data-ttu-id="6ac1f-225">Ahora, actualice el código del proveedor mediante el siguiente script:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-225">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="6ac1f-226">Este script genera un número aleatorio y actualiza el código del proveedor en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-226">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="6ac1f-227">Con `DebugMode` establecido en false, el contenido del archivo "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nunca cambia.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-227">With `DebugMode` set to false, the contents of the file “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” are never changed.</span></span>

<span data-ttu-id="6ac1f-228">Ahora, establezca `DebugMode` en **TRUE** en el script de configuración:</span><span class="sxs-lookup"><span data-stu-id="6ac1f-228">Now, set `DebugMode` to **TRUE** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

<span data-ttu-id="6ac1f-229">Cuando vuelva a ejecutar el script anterior, verá que el contenido del archivo es cada vez distinto.</span><span class="sxs-lookup"><span data-stu-id="6ac1f-229">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="6ac1f-230">(Puede ejecutar `Get-DscConfiguration` para comprobarlo).</span><span class="sxs-lookup"><span data-stu-id="6ac1f-230">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="6ac1f-231">A continuación se muestra el resultado de dos ejecuciones adicionales (los resultados pueden ser diferentes cuando ejecute el script):</span><span class="sxs-lookup"><span data-stu-id="6ac1f-231">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14                                      localhost
```

## <a name="see-also"></a><span data-ttu-id="6ac1f-232">Véase también</span><span class="sxs-lookup"><span data-stu-id="6ac1f-232">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="6ac1f-233">Referencia</span><span class="sxs-lookup"><span data-stu-id="6ac1f-233">Reference</span></span>
* [<span data-ttu-id="6ac1f-234">Recurso de DSC Log</span><span class="sxs-lookup"><span data-stu-id="6ac1f-234">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="6ac1f-235">Conceptos</span><span class="sxs-lookup"><span data-stu-id="6ac1f-235">Concepts</span></span>
* [<span data-ttu-id="6ac1f-236">Crear recursos de configuración de estado deseado de Windows PowerShell personalizados</span><span class="sxs-lookup"><span data-stu-id="6ac1f-236">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="6ac1f-237">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="6ac1f-237">Other Resources</span></span>
* [<span data-ttu-id="6ac1f-238">Cmdlets de configuración de estado deseado (DSC) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ac1f-238">Windows PowerShell Desired State Configuration Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)

