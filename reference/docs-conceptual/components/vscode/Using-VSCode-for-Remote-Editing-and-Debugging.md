---
title: Uso de Visual Studio Code para la edición y la depuración de forma remota
description: Uso de Visual Studio Code para la edición y la depuración de forma remota
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263932"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="2d003-103">Uso de Visual Studio Code para la edición y la depuración de forma remota</span><span class="sxs-lookup"><span data-stu-id="2d003-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="2d003-104">Aquellos usuarios que están familiarizados con el ISE pueden recordar que era posible ejecutar `psedit file.ps1` desde la consola integrada para abrir archivos, locales o remotos, directamente en el ISE.</span><span class="sxs-lookup"><span data-stu-id="2d003-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="2d003-105">Esta característica también está disponible en la extensión de PowerShell para VSCode.</span><span class="sxs-lookup"><span data-stu-id="2d003-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="2d003-106">Esta guía muestra cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="2d003-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2d003-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="2d003-107">Prerequisites</span></span>

<span data-ttu-id="2d003-108">En esta guía se da por supuesto que tiene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2d003-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="2d003-109">un recurso remoto (p. ej.: una máquina virtual, un contenedor) al que tiene acceso.</span><span class="sxs-lookup"><span data-stu-id="2d003-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="2d003-110">PowerShell ejecutándose en él y en el equipo host</span><span class="sxs-lookup"><span data-stu-id="2d003-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="2d003-111">VSCode y la extensión de PowerShell para VSCode</span><span class="sxs-lookup"><span data-stu-id="2d003-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="2d003-112">Esta característica funciona en Windows PowerShell y PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2d003-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="2d003-113">Esta característica también funciona al conectarse a un equipo remoto a través de WinRM, PowerShell Direct o SSH.</span><span class="sxs-lookup"><span data-stu-id="2d003-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="2d003-114">Si desea usar SSH, pero está usando Windows, consulte la [versión Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="2d003-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d003-115">Los comandos `Open-EditorFile` y `psedit` solo funcionan en la **consola integrada de PowerShell** que la extensión de PowerShell crea para VSCode.</span><span class="sxs-lookup"><span data-stu-id="2d003-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="2d003-116">Ejemplos de uso</span><span class="sxs-lookup"><span data-stu-id="2d003-116">Usage examples</span></span>

<span data-ttu-id="2d003-117">Estos ejemplos muestran la depuración y la edición remotas desde un equipo MacBook Pro a una máquina virtual Ubuntu que se ejecuta en Azure.</span><span class="sxs-lookup"><span data-stu-id="2d003-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="2d003-118">El proceso es idéntico en Windows.</span><span class="sxs-lookup"><span data-stu-id="2d003-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="2d003-119">Edición de archivo local con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="2d003-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="2d003-120">Con la extensión de PowerShell para VSCode iniciada y la consola integrada de PowerShell abierta, podemos escribir `Open-EditorFile foo.ps1` o `psedit foo.ps1` para abrir el archivo foo.ps1 local directamente en el editor.</span><span class="sxs-lookup"><span data-stu-id="2d003-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 funciona localmente](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="2d003-122">El archivo `foo.ps1` ya debería existir.</span><span class="sxs-lookup"><span data-stu-id="2d003-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="2d003-123">Desde ahí, podemos hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2d003-123">From there, we can:</span></span>

- <span data-ttu-id="2d003-124">Agregar puntos de interrupción en el medianil.</span><span class="sxs-lookup"><span data-stu-id="2d003-124">Add breakpoints to the gutter</span></span>

  ![agregar punto de interrupción en el medianil](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="2d003-126">Presionar F5 para depurar el script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d003-126">Hit F5 to debug the PowerShell script.</span></span>

  ![depurar el script local de PowerShell](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="2d003-128">Durante la depuración, puede interactuar con la consola de depuración y consultar las variables en el ámbito de la izquierda y todas las demás herramientas de depuración estándar.</span><span class="sxs-lookup"><span data-stu-id="2d003-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="2d003-129">Edición de archivo remoto con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="2d003-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="2d003-130">Ahora veamos la edición y la depuración de un archivo remoto.</span><span class="sxs-lookup"><span data-stu-id="2d003-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="2d003-131">Los pasos son prácticamente los mismos, solo hay una cosa que debemos hacer primero: escribir nuestra sesión de PowerShell en el servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="2d003-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="2d003-132">Hay un cmdlet para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="2d003-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="2d003-133">Se llama `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="2d003-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="2d003-134">La explicación desglosada del cmdlet es:</span><span class="sxs-lookup"><span data-stu-id="2d003-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="2d003-135">`Enter-PSSession -ComputerName foo` inicia una sesión a través de WinRM</span><span class="sxs-lookup"><span data-stu-id="2d003-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="2d003-136">`Enter-PSSession -ContainerId foo` y `Enter-PSSession -VmId foo` inician una sesión a través de PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="2d003-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="2d003-137">`Enter-PSSession -HostName foo` inicia una sesión a través de SSH</span><span class="sxs-lookup"><span data-stu-id="2d003-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="2d003-138">Para más información, consulte la documentación para [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="2d003-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="2d003-139">Como vamos desde macOS a una máquina virtual Ubuntu en Azure, usamos SSH para la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="2d003-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="2d003-140">En primer lugar, ejecute `Enter-PSSession` en la consola integrada.</span><span class="sxs-lookup"><span data-stu-id="2d003-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="2d003-141">Se conecta a la sesión remota cuando `[<hostname>]` aparece a la izquierda del símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="2d003-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![La llamada a Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="2d003-143">Ahora, podemos completar los mismos pasos que llevaríamos a cabo si estuviéramos editando un script local.</span><span class="sxs-lookup"><span data-stu-id="2d003-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="2d003-144">Ejecute `Open-EditorFile test.ps1` o `psedit test.ps1` para abrir el archivo `test.ps1` remoto.</span><span class="sxs-lookup"><span data-stu-id="2d003-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![El archivo test.ps1 Open-EditorFile](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="2d003-146">Editar el archivo/establecer los puntos de interrupción</span><span class="sxs-lookup"><span data-stu-id="2d003-146">Edit the file/set breakpoints</span></span>

   ![edición y establecimiento de puntos de interrupción](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="2d003-148">Iniciar la depuración (F5) del archivo remoto</span><span class="sxs-lookup"><span data-stu-id="2d003-148">Start debugging (F5) the remote file</span></span>

   ![depuración del archivo remoto](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="2d003-150">Si tiene algún problema, puede abrir los problemas que hay en el [repositorio de GitHub](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="2d003-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
