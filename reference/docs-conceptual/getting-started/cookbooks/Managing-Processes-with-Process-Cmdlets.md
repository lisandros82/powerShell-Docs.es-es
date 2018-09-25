---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administración de procesos con cmdlets de proceso
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: 417b5a40cde51029de9ed8e005732978d92c9057
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46013148"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="19b55-103">Administración de procesos con cmdlets de proceso</span><span class="sxs-lookup"><span data-stu-id="19b55-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="19b55-104">Puede usar los cmdlets Process en Windows PowerShell para administrar procesos locales y remotos en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19b55-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="19b55-105">Obtener procesos (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="19b55-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="19b55-106">Para obtener los procesos que se están ejecutando en el equipo local, ejecute **Get-Process** sin parámetros.</span><span class="sxs-lookup"><span data-stu-id="19b55-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="19b55-107">Puede obtener determinados procesos especificando sus nombres de proceso o identificadores de proceso.</span><span class="sxs-lookup"><span data-stu-id="19b55-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="19b55-108">El siguiente comando obtiene el proceso inactivo:</span><span class="sxs-lookup"><span data-stu-id="19b55-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="19b55-109">Aunque es normal que los cmdlets no devuelvan datos en algunas situaciones, cuando se especifica un proceso por su id. de proceso **Get-Process**, genera un error si no encuentra ninguna coincidencia, porque la intención habitual consiste en recuperar un proceso en ejecución conocido.</span><span class="sxs-lookup"><span data-stu-id="19b55-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="19b55-110">Si no hay ningún proceso con ese identificador, es probable que el identificador sea incorrecto o que el proceso de interés haya terminado:</span><span class="sxs-lookup"><span data-stu-id="19b55-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="19b55-111">Puede usar el parámetro Name del cmdlet Get-Process para especificar un subconjunto de procesos basado en el nombre del proceso.</span><span class="sxs-lookup"><span data-stu-id="19b55-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="19b55-112">El parámetro Name puede tomar varios nombres de una lista de nombres separados por comas y admite el uso de caracteres comodín, para que pueda escribir patrones de nombre.</span><span class="sxs-lookup"><span data-stu-id="19b55-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="19b55-113">Por ejemplo, el siguiente comando obtiene el proceso cuyos nombres comienzan por "ex".</span><span class="sxs-lookup"><span data-stu-id="19b55-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="19b55-114">Dado que la clase System.Diagnostics.Process de .NET es la base de los procesos de Windows PowerShell, sigue algunas de las convenciones usadas por System.Diagnostics.Process.</span><span class="sxs-lookup"><span data-stu-id="19b55-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="19b55-115">Una de estas convenciones es que el nombre de proceso de un archivo ejecutable nunca incluya ".exe" al final del nombre del ejecutable.</span><span class="sxs-lookup"><span data-stu-id="19b55-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="19b55-116">**Get-Process** también acepta varios valores para el parámetro Name.</span><span class="sxs-lookup"><span data-stu-id="19b55-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="19b55-117">Puede usar el parámetro ComputerName de Get-Process para obtener procesos en equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="19b55-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="19b55-118">Por ejemplo, el comando siguiente obtiene los procesos de PowerShell en el equipo local (representado por "localhost") y en dos equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="19b55-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="19b55-119">Los nombres de equipo no son evidentes en esta presentación, pero se almacenan en la propiedad MachineName de los objetos de proceso que devuelve Get-Process.</span><span class="sxs-lookup"><span data-stu-id="19b55-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="19b55-120">El siguiente comando usa el cmdlet Format-Table para mostrar el identificador de proceso y las propiedades ProcessName y MachineName (ComputerName) de los objetos de proceso.</span><span class="sxs-lookup"><span data-stu-id="19b55-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="19b55-121">Este comando más complejo agrega la propiedad MachineName a la presentación estándar de Get-Process.</span><span class="sxs-lookup"><span data-stu-id="19b55-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="19b55-122">Detener procesos (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="19b55-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="19b55-123">Windows PowerShell ofrece flexibilidad para enumerar procesos, pero ¿qué hay de detenerlos?</span><span class="sxs-lookup"><span data-stu-id="19b55-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="19b55-124">El cmdlet **Stop-Process** toma un nombre o un identificador para especificar un proceso que quiere detener.</span><span class="sxs-lookup"><span data-stu-id="19b55-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="19b55-125">Su capacidad para detener procesos dependerá de sus permisos.</span><span class="sxs-lookup"><span data-stu-id="19b55-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="19b55-126">Algunos procesos no se pueden detener.</span><span class="sxs-lookup"><span data-stu-id="19b55-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="19b55-127">Por ejemplo, si intenta detener el proceso inactivo, obtendrá un error:</span><span class="sxs-lookup"><span data-stu-id="19b55-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="19b55-128">También puede forzar la solicitud con el parámetro **Confirm**.</span><span class="sxs-lookup"><span data-stu-id="19b55-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="19b55-129">Este parámetro es especialmente útil si se usa un carácter comodín al especificar el nombre del proceso, ya que accidentalmente podría coincidir con algunos procesos que no quiere detener:</span><span class="sxs-lookup"><span data-stu-id="19b55-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="19b55-130">La manipulación de procesos complejos es posible si se usan algunos cmdlets de filtrado de objetos.</span><span class="sxs-lookup"><span data-stu-id="19b55-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="19b55-131">Dado que un objeto Process tiene una propiedad Responding que es true cuando ya no responde, puede detener todas las aplicaciones que no respondan con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="19b55-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="19b55-132">Puede usar el mismo enfoque en otras situaciones.</span><span class="sxs-lookup"><span data-stu-id="19b55-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="19b55-133">Por ejemplo, supongamos que una aplicación de área de notificaciones secundaria se ejecuta automáticamente cuando los usuarios inician otra aplicación.</span><span class="sxs-lookup"><span data-stu-id="19b55-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="19b55-134">Es posible que esto no funcione correctamente en las sesiones de Terminal Services, pero lo quiera seguir manteniendo en las sesiones que se ejecutan en la consola del equipo físico.</span><span class="sxs-lookup"><span data-stu-id="19b55-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="19b55-135">Las sesiones conectadas en el escritorio del equipo físico siempre tienen un identificador de la sesión 0, por lo que puede detener todas las instancias del proceso que están en otras sesiones mediante **Where-Object** y el proceso, **SessionId**:</span><span class="sxs-lookup"><span data-stu-id="19b55-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="19b55-136">El cmdlet Stop-Process no tiene un parámetro ComputerName.</span><span class="sxs-lookup"><span data-stu-id="19b55-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="19b55-137">Por lo tanto, para ejecutar un comando para detener un proceso en un equipo remoto, debe usar el cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="19b55-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="19b55-138">Por ejemplo, para detener el proceso de PowerShell en el equipo remoto Server01, escriba:</span><span class="sxs-lookup"><span data-stu-id="19b55-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="19b55-139">Detener todas las demás sesiones de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="19b55-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="19b55-140">En ocasiones puede ser útil poder detener todas las sesiones de Windows PowerShell que se están ejecutando, excepto la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="19b55-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="19b55-141">Si una sesión usa demasiados recursos o es inaccesible (quizás se esté ejecutando de forma remota o en otra sesión de escritorio), es posible que no pueda detenerla directamente.</span><span class="sxs-lookup"><span data-stu-id="19b55-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="19b55-142">Si intenta detener todas las sesiones que se están ejecutando, la sesión actual podría finalizar en su lugar.</span><span class="sxs-lookup"><span data-stu-id="19b55-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="19b55-143">Cada sesión de Windows PowerShell tiene un PID de variable de entorno que contiene el identificador del proceso de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19b55-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="19b55-144">Puede comprobar el $PID con el identificador de cada sesión y finalizar solo las sesiones de Windows PowerShell que tengan un identificador diferente. El siguiente comando de canalización realiza esta acción y devuelve la lista de las sesiones finalizadas (debido al uso del parámetro **PassThru**):</span><span class="sxs-lookup"><span data-stu-id="19b55-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="19b55-145">Iniciar, depurar y esperar procesos</span><span class="sxs-lookup"><span data-stu-id="19b55-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="19b55-146">Windows PowerShell también incluye cmdlets para iniciar (o reiniciar) y depurar un proceso, así como para esperar a que un proceso se complete antes de ejecutar un comando.</span><span class="sxs-lookup"><span data-stu-id="19b55-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="19b55-147">Para obtener información acerca de estos cmdlets, vea el tema de ayuda de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19b55-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="19b55-148">Véase también</span><span class="sxs-lookup"><span data-stu-id="19b55-148">See Also</span></span>

- <span data-ttu-id="19b55-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="19b55-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="19b55-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="19b55-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="19b55-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="19b55-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="19b55-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="19b55-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="19b55-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="19b55-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="19b55-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="19b55-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
