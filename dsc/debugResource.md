---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Depuración de recursos de DSC"
ms.openlocfilehash: c9534deb755e2d3ce59dbb44e55b58b59af2e7f4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="3cfe5-103">Depuración de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="3cfe5-103">Debugging DSC resources</span></span>

> <span data-ttu-id="3cfe5-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3cfe5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3cfe5-105">En PowerShell 5.0, se introdujo una nueva característica en la configuración de estado deseado (DSC) que permite depurar un recurso de DSC mientras se aplica una configuración.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="3cfe5-106">Habilitar la depuración de DSC</span><span class="sxs-lookup"><span data-stu-id="3cfe5-106">Enabling DSC debugging</span></span>
<span data-ttu-id="3cfe5-107">Antes de poder depurar un recurso, tendrá que habilitar la depuración mediante una llamada al cmdlet [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cfe5-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span> <span data-ttu-id="3cfe5-108">Este cmdlet toma un parámetro obligatorio, **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span> 

<span data-ttu-id="3cfe5-109">Puede comprobar que se ha habilitado la depuración si examina el resultado de una llamada a [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cfe5-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="3cfe5-110">En la siguiente salida de PowerShell se muestra el resultado de la habilitación de la depuración:</span><span class="sxs-lookup"><span data-stu-id="3cfe5-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="3cfe5-111">Iniciar una configuración con la depuración habilitada</span><span class="sxs-lookup"><span data-stu-id="3cfe5-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="3cfe5-112">Para depurar un recurso de DSC, debe iniciar una configuración que llame a ese recurso.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span> <span data-ttu-id="3cfe5-113">En este ejemplo, se examinará una configuración simple que llama al recurso [WindowsFeature](windowsfeatureResource.md) para garantizar que se instale la característica "WindowsPowerShellWebAccess":</span><span class="sxs-lookup"><span data-stu-id="3cfe5-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="3cfe5-114">Después de compilar la configuración, iníciela mediante una llamada a [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cfe5-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span> <span data-ttu-id="3cfe5-115">La configuración se detendrá cuando el administrador de configuración local (LCM) llame al primer recurso de la configuración.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span> <span data-ttu-id="3cfe5-116">Si usa los parámetros `-Verbose` y `-Wait`, la salida mostrará las líneas que se deben especificar para iniciar la depuración.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will 
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach. 
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="3cfe5-117">En este punto, el LCM ha llamado al recurso y alcanza el primer punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-117">At this point, the LCM has called the resource, and come to the first break point.</span></span> <span data-ttu-id="3cfe5-118">En las tres últimas líneas de la salida se muestra cómo adjuntarse al proceso y empezar a depurar el script del recurso.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="3cfe5-119">Depuración del script del recurso</span><span class="sxs-lookup"><span data-stu-id="3cfe5-119">Debugging the resource script</span></span>

<span data-ttu-id="3cfe5-120">Inicie una nueva instancia de PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-120">Start a new instance of the PowerShell ISE.</span></span> <span data-ttu-id="3cfe5-121">En el panel de la consola, escriba las tres últimas líneas de la salida `Start-DscConfiguration` como comandos, reemplazando `<credentials>` por credenciales de usuario válidas.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span> <span data-ttu-id="3cfe5-122">Ahora debería ver un aviso parecido a:</span><span class="sxs-lookup"><span data-stu-id="3cfe5-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="3cfe5-123">El script de recursos se abrirá en el panel de scripts y el depurador se detendrá en la primera línea de la función **Test-TargetResource** (el método **Test()** de un recurso basado en clases).</span><span class="sxs-lookup"><span data-stu-id="3cfe5-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="3cfe5-124">Ahora, puede utilizar los comandos de depuración en el ISE para seguir los pasos del script de recursos, consultar valores variables, ver la pila de llamadas, etc.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="3cfe5-125">Para obtener más información sobre la depuración en PowerShell ISE, vea [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx) (Cómo depurar scripts de Windows PowerShell ISE).</span><span class="sxs-lookup"><span data-stu-id="3cfe5-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span> <span data-ttu-id="3cfe5-126">Recuerde que cada línea del script de recursos (o clase) se define como un punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="3cfe5-127">Deshabilitar la depuración de DSC</span><span class="sxs-lookup"><span data-stu-id="3cfe5-127">Disabling DSC debugging</span></span>

<span data-ttu-id="3cfe5-128">Después de llamar a [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), todas las llamadas a [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) darán como resultado que la configuración interrumpa al depurador.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="3cfe5-129">Para permitir que las configuraciones sigan ejecutándose con normalidad, debe deshabilitar la depuración mediante una llamada al cmdlet [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx).</span><span class="sxs-lookup"><span data-stu-id="3cfe5-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="3cfe5-130">**Nota:** Reiniciar no cambia el estado de depuración del LCM.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="3cfe5-131">Si está habilitada la depuración, iniciar una configuración seguirá interrumpiendo el depurador tras reiniciar.</span><span class="sxs-lookup"><span data-stu-id="3cfe5-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="3cfe5-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="3cfe5-132">See Also</span></span>
- [<span data-ttu-id="3cfe5-133">Escribir un recurso de DSC personalizado con MOF</span><span class="sxs-lookup"><span data-stu-id="3cfe5-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="3cfe5-134">Escribir un recurso de DSC personalizado con clases de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cfe5-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)

