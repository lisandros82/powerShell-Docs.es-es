---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Cambiar el estado del equipo
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736920"
---
# <a name="changing-computer-state"></a><span data-ttu-id="48896-103">Cambiar el estado del equipo</span><span class="sxs-lookup"><span data-stu-id="48896-103">Changing Computer State</span></span>

<span data-ttu-id="48896-104">Para restablecer un equipo en PowerShell, use una herramienta de línea de comandos estándar, WMI o una clase CIM.</span><span class="sxs-lookup"><span data-stu-id="48896-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="48896-105">Aunque use PowerShell solo para ejecutar la herramienta, aprender a cambiar el estado de energía de un equipo en PowerShell le mostrará algunos de los detalles importantes sobre el uso de herramientas externas en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48896-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="48896-106">Bloquear un equipo</span><span class="sxs-lookup"><span data-stu-id="48896-106">Locking a Computer</span></span>

<span data-ttu-id="48896-107">La única manera de bloquear un equipo directamente con las herramientas estándar disponibles es llamar a la función **LockWorkstation()** en **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="48896-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="48896-108">Este comando bloquea inmediatamente la estación de trabajo.</span><span class="sxs-lookup"><span data-stu-id="48896-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="48896-109">Usa **rundll32.exe**, que ejecuta archivos DLL de Windows (y guarda sus bibliotecas para usarlas repetidamente), para ejecutar `user32.dll`, una biblioteca de funciones de administración de Windows.</span><span class="sxs-lookup"><span data-stu-id="48896-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="48896-110">Si se bloquea una estación de trabajo mientras Cambio rápido de usuario está habilitado, como en Windows XP, el equipo muestra la pantalla de inicio de sesión de usuario, en lugar de iniciar el protector de pantalla del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="48896-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="48896-111">Para cerrar sesiones determinadas en un servidor de Terminal Server, use la herramienta de línea de comandos **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="48896-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="48896-112">Cerrar la sesión actual</span><span class="sxs-lookup"><span data-stu-id="48896-112">Logging Off the Current Session</span></span>

<span data-ttu-id="48896-113">Puede usar varias técnicas diferentes para cerrar una sesión en el sistema local.</span><span class="sxs-lookup"><span data-stu-id="48896-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="48896-114">La manera más sencilla es usar la herramienta de línea de comandos **logoff.exe** de Escritorio remoto/Terminal Services (para obtener más información, en el símbolo del sistema de PowerShell, escriba `logoff /?`).</span><span class="sxs-lookup"><span data-stu-id="48896-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="48896-115">Para cerrar la sesión activa actualmente, escriba `logoff` sin argumentos.</span><span class="sxs-lookup"><span data-stu-id="48896-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="48896-116">También puede usar la herramienta **shutdown.exe** con su opción de cierre de sesión:</span><span class="sxs-lookup"><span data-stu-id="48896-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="48896-117">Otra opción es usar WMI.</span><span class="sxs-lookup"><span data-stu-id="48896-117">Another option is to use WMI.</span></span> <span data-ttu-id="48896-118">La clase **Win32_OperatingSystem** tiene un método **Shutdown**.</span><span class="sxs-lookup"><span data-stu-id="48896-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="48896-119">Al invocar el método con la marca 0 se inicia el cierre de sesión:</span><span class="sxs-lookup"><span data-stu-id="48896-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="48896-120">Para más información sobre el método **Shutdown**, consulte [Método Shutdown de la clase Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem).</span><span class="sxs-lookup"><span data-stu-id="48896-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="48896-121">Apagar o reiniciar un equipo</span><span class="sxs-lookup"><span data-stu-id="48896-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="48896-122">Apagar y reiniciar equipos suelen ser los mismos tipos de tarea.</span><span class="sxs-lookup"><span data-stu-id="48896-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="48896-123">Las herramientas que apagan un equipo generalmente también lo reinician, y viceversa.</span><span class="sxs-lookup"><span data-stu-id="48896-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="48896-124">Hay dos opciones sencillas para reiniciar un equipo desde PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48896-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="48896-125">Use **tsshutdn.exe** o **shutdown.exe** con los argumentos apropiados.</span><span class="sxs-lookup"><span data-stu-id="48896-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="48896-126">Puede obtener información de uso detallada en `tsshutdn.exe /?` o `shutdown.exe /?`.</span><span class="sxs-lookup"><span data-stu-id="48896-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="48896-127">También puede realizar las operaciones de apagar y reiniciar directamente desde PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48896-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="48896-128">Para apagar el equipo, use el comando Stop-Computer.</span><span class="sxs-lookup"><span data-stu-id="48896-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="48896-129">Para reiniciar el sistema operativo, use el comando Restart-Computer.</span><span class="sxs-lookup"><span data-stu-id="48896-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="48896-130">Para forzar un reinicio inmediato del equipo, use el parámetro -Force.</span><span class="sxs-lookup"><span data-stu-id="48896-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
