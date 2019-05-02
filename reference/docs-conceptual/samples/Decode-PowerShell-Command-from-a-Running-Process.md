---
ms.date: 11/13/2018
keywords: powershell, cmdlet
title: Descodificación de un comando de PowerShell desde un proceso en ejecución
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086245"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="ff399-103">Descodificación de un comando de PowerShell desde un proceso en ejecución</span><span class="sxs-lookup"><span data-stu-id="ff399-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="ff399-104">En ocasiones, puede tener un proceso en ejecución que ocupa una gran cantidad de recursos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff399-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="ff399-105">Este proceso podría ejecutarse en el contexto de un trabajo del [Programador de tareas][] o el [Agente SQL Server][].</span><span class="sxs-lookup"><span data-stu-id="ff399-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="ff399-106">Cuando hay varios procesos de PowerShell en ejecución, puede ser difícil saber qué proceso representa el problema.</span><span class="sxs-lookup"><span data-stu-id="ff399-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="ff399-107">En este artículo se muestra cómo descodificar un bloque de script que se está ejecutando un proceso de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff399-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="ff399-108">Creación de un proceso de larga duración</span><span class="sxs-lookup"><span data-stu-id="ff399-108">Create a long running process</span></span>

<span data-ttu-id="ff399-109">Para demostrar este escenario, abra una nueva ventana de PowerShell y ejecute el siguiente código.</span><span class="sxs-lookup"><span data-stu-id="ff399-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="ff399-110">Ejecuta un comando de PowerShell que da como resultado un número cada minuto durante 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="ff399-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="ff399-111">Visualización del proceso</span><span class="sxs-lookup"><span data-stu-id="ff399-111">View the process</span></span>

<span data-ttu-id="ff399-112">El cuerpo del comando que PowerShell está ejecutando se almacena en la propiedad **CommandLine** de la clase [Win32_Process][].</span><span class="sxs-lookup"><span data-stu-id="ff399-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="ff399-113">Si el comando es un [comando codificado][], la propiedad **CommandLine** contiene la cadena "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="ff399-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="ff399-114">Con esta información, el comando codificado puede ser desofuscado mediante el siguiente proceso.</span><span class="sxs-lookup"><span data-stu-id="ff399-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="ff399-115">Inicie PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="ff399-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="ff399-116">Es vital que PowerShell se esté ejecutando como administrador; de lo contrario, no se obtienen resultados al consultar los procesos en ejecución.</span><span class="sxs-lookup"><span data-stu-id="ff399-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="ff399-117">Ejecute el siguiente comando para obtener todos los procesos de PowerShell que tienen un comando codificado:</span><span class="sxs-lookup"><span data-stu-id="ff399-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="ff399-118">El siguiente comando crea un objeto de PowerShell personalizado que contiene el identificador de proceso y el comando codificado.</span><span class="sxs-lookup"><span data-stu-id="ff399-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="ff399-119">Ahora se puede descodificar el comando codificado.</span><span class="sxs-lookup"><span data-stu-id="ff399-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="ff399-120">El fragmento de código siguiente recorre en iteración el objeto de detalles del comando, descodifica el comando codificado y agrega de nuevo el comando descodificado al objeto para seguir investigándolo.</span><span class="sxs-lookup"><span data-stu-id="ff399-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="ff399-121">Ahora se puede revisar el comando descodificado seleccionando la propiedad del comando descodificado.</span><span class="sxs-lookup"><span data-stu-id="ff399-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Programador de tareas]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Agente SQL Server]: /sql/ssms/agent/sql-server-agent
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[comando codificado]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
