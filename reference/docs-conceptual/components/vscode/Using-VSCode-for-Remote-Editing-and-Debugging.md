---
title: Uso de Visual Studio Code para la edición y la depuración de forma remota
description: Uso de Visual Studio Code para la edición y la depuración de forma remota
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086684"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="d675a-103">Uso de Visual Studio Code para la edición y la depuración de forma remota</span><span class="sxs-lookup"><span data-stu-id="d675a-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="d675a-104">Aquellos usuarios que estuvieran familiarizados con el ISE pueden recordar que era posible ejecutar `psedit file.ps1` desde la consola integrada para abrir archivos, locales o remotos, directamente en el ISE.</span><span class="sxs-lookup"><span data-stu-id="d675a-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="d675a-105">Resulta que esta característica también está disponible en la extensión de PowerShell para VSCode.</span><span class="sxs-lookup"><span data-stu-id="d675a-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="d675a-106">Esta guía le mostrará cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="d675a-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d675a-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="d675a-107">Prerequisites</span></span>

<span data-ttu-id="d675a-108">En esta guía se da por supuesto que tiene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d675a-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="d675a-109">un recurso remoto (p. ej.: una máquina virtual, un contenedor) al que tiene acceso</span><span class="sxs-lookup"><span data-stu-id="d675a-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="d675a-110">PowerShell ejecutándose en él y en el equipo host</span><span class="sxs-lookup"><span data-stu-id="d675a-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="d675a-111">VSCode y la extensión de PowerShell para VSCode</span><span class="sxs-lookup"><span data-stu-id="d675a-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="d675a-112">Esta característica funciona en Windows PowerShell y PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="d675a-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="d675a-113">Esta característica también funciona al conectarse a un equipo remoto a través de WinRM, PowerShell Direct o SSH.</span><span class="sxs-lookup"><span data-stu-id="d675a-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="d675a-114">Si desea usar SSH, pero está usando Windows, consulte la [versión Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="d675a-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="d675a-115">Empecemos</span><span class="sxs-lookup"><span data-stu-id="d675a-115">Let's go</span></span>

<span data-ttu-id="d675a-116">En esta sección, le guiaré por la edición y depuración remotas desde mi MacBook Pro en una máquina virtual de Ubuntu que se ejecuta en Azure.</span><span class="sxs-lookup"><span data-stu-id="d675a-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="d675a-117">Aunque no use Windows, **el proceso es idéntico**.</span><span class="sxs-lookup"><span data-stu-id="d675a-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="d675a-118">Edición de archivo local con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="d675a-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="d675a-119">Con la extensión de PowerShell para VSCode iniciada y la consola integrada de PowerShell abierta, podemos escribir `Open-EditorFile foo.ps1` o `psedit foo.ps1` para abrir el archivo foo.ps1 local directamente en el editor.</span><span class="sxs-lookup"><span data-stu-id="d675a-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="d675a-121">foo.ps1 ya debe existir.</span><span class="sxs-lookup"><span data-stu-id="d675a-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="d675a-122">Desde ahí, podemos hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d675a-122">From there, we can:</span></span>

<span data-ttu-id="d675a-123">agregar puntos de interrupción en el medianil ![adición de punto de interrupción en el medianil](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="d675a-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="d675a-124">y presionar la tecla F5 para depurar el script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d675a-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="d675a-125">![depuración del script de PowerShell local](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="d675a-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="d675a-126">Durante la depuración, puede interactuar con la consola de depuración y consultar las variables en el ámbito de la izquierda y todas las demás herramientas de depuración estándar.</span><span class="sxs-lookup"><span data-stu-id="d675a-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="d675a-127">Edición de archivo remoto con Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="d675a-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="d675a-128">Ahora veamos la edición y la depuración de un archivo remoto.</span><span class="sxs-lookup"><span data-stu-id="d675a-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="d675a-129">Los pasos son prácticamente los mismos, solo hay una cosa que debemos hacer primero: escribir nuestra sesión de PowerShell en el servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="d675a-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="d675a-130">Hay un cmdlet para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="d675a-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="d675a-131">Se llama `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d675a-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="d675a-132">La explicación desglosada del cmdlet es:</span><span class="sxs-lookup"><span data-stu-id="d675a-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="d675a-133">`Enter-PSSession -ComputerName foo` inicia una sesión a través de WinRM</span><span class="sxs-lookup"><span data-stu-id="d675a-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="d675a-134">`Enter-PSSession -ContainerId foo` y `Enter-PSSession -VmId foo` inician una sesión a través de PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="d675a-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="d675a-135">`Enter-PSSession -HostName foo` inicia una sesión a través de SSH</span><span class="sxs-lookup"><span data-stu-id="d675a-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="d675a-136">Para obtener más información sobre `Enter-PSSession`, consulte los documentos [aquí](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="d675a-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="d675a-137">Usaré SSH para la comunicación remota porque parto de macOS para llegar a una máquina virtual de Ubuntu en Azure.</span><span class="sxs-lookup"><span data-stu-id="d675a-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="d675a-138">En primer lugar, en la consola integrada, vamos a ejecutar nuestro Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="d675a-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="d675a-139">Sabrá que se encuentra en la sesión porque aparecerá `[something]` a la izquierda del mensaje.</span><span class="sxs-lookup"><span data-stu-id="d675a-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![La llamada a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="d675a-141">Desde ahí, podemos seguir los pasos exactos como si estuviéramos editando un script local.</span><span class="sxs-lookup"><span data-stu-id="d675a-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="d675a-142">Ejecutar `Open-EditorFile test.ps1` o `psedit test.ps1` para abrir el archivo remoto `test.ps1` ![Aplicación de Open-EditorFile al archivo test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="d675a-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="d675a-143">Editar el archivo/establecer los puntos de interrupción</span><span class="sxs-lookup"><span data-stu-id="d675a-143">Edit the file/set breakpoints</span></span> ![edición y establecimiento de puntos de interrupción](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="d675a-145">Iniciar la depuración (F5) del archivo remoto</span><span class="sxs-lookup"><span data-stu-id="d675a-145">Start debugging (F5) the remote file</span></span>

![depuración del archivo remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="d675a-147">¡Eso es todo esto!</span><span class="sxs-lookup"><span data-stu-id="d675a-147">That's all there's to it!</span></span> <span data-ttu-id="d675a-148">Esperamos que esta guía haya ayudado a resolver cualquier duda sobre la depuración y la edición remota de PowerShell en VSCode.</span><span class="sxs-lookup"><span data-stu-id="d675a-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="d675a-149">Si tiene problemas, no dude en plantearlas [en el repositorio de GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="d675a-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
