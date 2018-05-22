---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="1b22c-102">Mejoras en la depuración de scripts de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b22c-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="1b22c-103">PowerShell 5.0 incluye varias mejoras para ofrecer una experiencia de depuración superior:</span><span class="sxs-lookup"><span data-stu-id="1b22c-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="1b22c-104">Interrumpir todos</span><span class="sxs-lookup"><span data-stu-id="1b22c-104">Break All</span></span>

<span data-ttu-id="1b22c-105">La consola de PowerShell y Windows PowerShell ISE permite ahora el acceso al depurador para ejecutar scripts.</span><span class="sxs-lookup"><span data-stu-id="1b22c-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="1b22c-106">Está opción está disponible para sesiones locales y remotas.</span><span class="sxs-lookup"><span data-stu-id="1b22c-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="1b22c-107">En la consola, presione **Ctrl+Interrumpir**.</span><span class="sxs-lookup"><span data-stu-id="1b22c-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="1b22c-108">En el ISE, presione **Ctrl+B** o use el comando de menú **Depurar -> Interrumpir todos**.</span><span class="sxs-lookup"><span data-stu-id="1b22c-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="1b22c-109">Depuración remota y edición remota de archivos en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1b22c-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="1b22c-110">Windows PowerShell ISE permite ahora abrir y editar archivos en una sesión remota mediante la ejecución del comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="1b22c-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="1b22c-111">Por ejemplo, puede abrir un archivo para editarlo desde la línea de comandos en una sesión remota de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="1b22c-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="1b22c-112">Además, ahora puede editarlo y guardar los cambios en un archivo remoto que se abrirá automáticamente en Windows PowerShell ISE cuando se alcance un punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="1b22c-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="1b22c-113">Ahora, puede depurar un archivo de script que se ejecute en un equipo remoto, editar el archivo para corregir un error y, después, volver a ejecutar el script modificado.</span><span class="sxs-lookup"><span data-stu-id="1b22c-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="1b22c-114">Depuración de scripts avanzada</span><span class="sxs-lookup"><span data-stu-id="1b22c-114">Advanced Script Debugging</span></span>

<span data-ttu-id="1b22c-115">Existen nuevas características de depuración avanzadas que permiten conectarse a cualquier proceso del equipo local que tenga Windows PowerShell cargado, así como depurar espacios de ejecución arbitrarios en ese proceso.</span><span class="sxs-lookup"><span data-stu-id="1b22c-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="1b22c-116">Depuración del espacio de ejecución</span><span class="sxs-lookup"><span data-stu-id="1b22c-116">Runspace Debugging</span></span>

<span data-ttu-id="1b22c-117">Los nuevos cmdlets agregados permiten enumerar los espacios de ejecución actuales en un proceso y conectar la consola de Windows PowerShell o el depurador de ISE a ese espacio de ejecución para la depuración de scripts:</span><span class="sxs-lookup"><span data-stu-id="1b22c-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="1b22c-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="1b22c-118">Get-Runspace</span></span>
-   <span data-ttu-id="1b22c-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="1b22c-119">Debug-Runspace</span></span>
-   <span data-ttu-id="1b22c-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="1b22c-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="1b22c-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="1b22c-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="1b22c-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="1b22c-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="1b22c-123">Conectarse al proceso que hospeda PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b22c-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="1b22c-124">Ahora puede establecer la conexión con cualquier proceso del equipo que tenga Windows PowerShell cargado.</span><span class="sxs-lookup"><span data-stu-id="1b22c-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="1b22c-125">Para ello, inicie una sesión interactiva con el proceso, como lo haría con una sesión remota interactiva ejecutando el cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="1b22c-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="1b22c-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="1b22c-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="1b22c-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="1b22c-127">Exit-PSHostProcess</span></span>
