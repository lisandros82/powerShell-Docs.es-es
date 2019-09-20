---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Mejoras en la depuración de scripts de PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147815"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="c4d5a-103">Mejoras en la depuración de scripts de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4d5a-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="c4d5a-104">PowerShell 5.0 incluye varias mejoras que perfeccionan la experiencia de depuración.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="c4d5a-105">Interrumpir todos</span><span class="sxs-lookup"><span data-stu-id="c4d5a-105">Break All</span></span>

<span data-ttu-id="c4d5a-106">La consola de PowerShell y PowerShell ISE permiten ahora el acceso al depurador para ejecutar scripts.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="c4d5a-107">Está opción está disponible para sesiones locales y remotas.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="c4d5a-108">En la consola, presione <kbd>Ctrl</kbd>+<kbd>Interrumpir</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="c4d5a-109">En el ISE, presione <kbd>Ctrl</kbd>+<kbd>B</kbd> o use el comando de menú **Depurar -> Interrumpir todos**.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="c4d5a-110">Depuración remota y edición remota de archivos en PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c4d5a-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="c4d5a-111">PowerShell ISE permite ahora abrir y editar archivos en una sesión remota mediante la ejecución del comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="c4d5a-112">Por ejemplo, puede abrir un archivo para editarlo desde la línea de comandos en una sesión remota de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="c4d5a-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="c4d5a-113">Además, ahora puede editarlo y guardar los cambios en un archivo remoto que se abrirá automáticamente en PowerShell ISE cuando se alcance un punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="c4d5a-114">Ahora, puede depurar un archivo de script que se ejecute en un equipo remoto, editar el archivo para corregir un error y, después, volver a ejecutar el script modificado.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="c4d5a-115">Depuración de scripts avanzada</span><span class="sxs-lookup"><span data-stu-id="c4d5a-115">Advanced Script Debugging</span></span>

<span data-ttu-id="c4d5a-116">Existen nuevas características de depuración avanzadas que permiten conectarse a cualquier proceso del equipo local que tenga PowerShell cargado, así como depurar espacios de ejecución arbitrarios en ese proceso.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="c4d5a-117">Depuración del espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="c4d5a-117">Runspace Debugging</span></span>

<span data-ttu-id="c4d5a-118">Los nuevos cmdlets agregados permiten enumerar los espacios de ejecución actuales en un proceso y conectar la consola de PowerShell o el depurador de PowerShell ISE a ese espacio de ejecución para la depuración de scripts:</span><span class="sxs-lookup"><span data-stu-id="c4d5a-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="c4d5a-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="c4d5a-119">Get-Runspace</span></span>
- <span data-ttu-id="c4d5a-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="c4d5a-120">Debug-Runspace</span></span>
- <span data-ttu-id="c4d5a-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="c4d5a-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="c4d5a-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="c4d5a-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="c4d5a-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="c4d5a-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="c4d5a-124">Conectarse al proceso que hospeda PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4d5a-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="c4d5a-125">Ahora puede establecer la conexión con cualquier proceso del equipo que tenga PowerShell cargado.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="c4d5a-126">Para ello, ingrese en una sesión interactiva con el proceso de host.</span><span class="sxs-lookup"><span data-stu-id="c4d5a-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="c4d5a-127">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="c4d5a-127">For more information, see:</span></span>

- [<span data-ttu-id="c4d5a-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="c4d5a-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="c4d5a-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="c4d5a-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
