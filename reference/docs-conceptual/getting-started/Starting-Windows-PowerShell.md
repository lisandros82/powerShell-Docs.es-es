---
ms.date: 12/05/2019
keywords: powershell, cmdlet
title: Iniciar Windows PowerShell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953830"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="e37b1-103">Iniciar Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e37b1-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="e37b1-104">Windows PowerShell es una `.DLL` de motor de scripting que se inserta en varios hosts.</span><span class="sxs-lookup"><span data-stu-id="e37b1-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="e37b1-105">Los hosts más comunes que iniciará son la línea de comandos interactiva **powershell.exe** y el entorno de scripting interactivo **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="e37b1-106">Para iniciar Windows PowerShell® en Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 y Windows 8, vea [Navegación y tareas de administración comunes en Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="e37b1-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="e37b1-107">PowerShell Core ha cambiado el nombre del archivo binario</span><span class="sxs-lookup"><span data-stu-id="e37b1-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="e37b1-108">PowerShell Core, al que se hace referencia como PowerShell, es la versión 6 y posterior, que es de código abierto y usa .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e37b1-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="e37b1-109">Las versiones admitidas están disponibles en Windows, macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="e37b1-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="e37b1-110">A partir de PowerShell 6, el nombre del archivo binario de PowerShell se ha cambiado por **pwsh.exe** para Windows y **pwsh** para macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="e37b1-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="e37b1-111">Puede iniciar versiones preliminares de PowerShell con **pwsh-preview**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="e37b1-112">Para más información, vea [Novedades de PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) y [Acerca de pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="e37b1-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="e37b1-113">Para encontrar la documentación de la instalación y la referencia de cmdlets de PowerShell 7, use los vínculos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e37b1-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="e37b1-114">Documento</span><span class="sxs-lookup"><span data-stu-id="e37b1-114">Document</span></span> | <span data-ttu-id="e37b1-115">Vínculo</span><span class="sxs-lookup"><span data-stu-id="e37b1-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="e37b1-116">Referencia de cmdlets</span><span class="sxs-lookup"><span data-stu-id="e37b1-116">Cmdlet reference</span></span> | [<span data-ttu-id="e37b1-117">Explorador de módulos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e37b1-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="e37b1-118">Instalación de Windows</span><span class="sxs-lookup"><span data-stu-id="e37b1-118">Windows installation</span></span> | [<span data-ttu-id="e37b1-119">Instalación de PowerShell Core en Windows</span><span class="sxs-lookup"><span data-stu-id="e37b1-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="e37b1-120">Instalación de macOS</span><span class="sxs-lookup"><span data-stu-id="e37b1-120">macOS installation</span></span> | [<span data-ttu-id="e37b1-121">Instalación de PowerShell Core en macOS</span><span class="sxs-lookup"><span data-stu-id="e37b1-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="e37b1-122">Instalación de Linux</span><span class="sxs-lookup"><span data-stu-id="e37b1-122">Linux installation</span></span> | [<span data-ttu-id="e37b1-123">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="e37b1-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="e37b1-124">Para ver el contenido de otras versiones de PowerShell, vea [Cómo usar la documentación de PowerShell](../how-to-use-docs.md).</span><span class="sxs-lookup"><span data-stu-id="e37b1-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="e37b1-125">Iniciar Windows PowerShell en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="e37b1-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="e37b1-126">En esta sección, se explica cómo iniciar Windows PowerShell y el Entorno de scripting integrado (ISE) de Windows PowerShell en Windows® 7, Windows Server® 2008 R2 y Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="e37b1-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="e37b1-127">También se explica cómo habilitar la característica opcional para Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server® 2008 R2 y Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="e37b1-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="e37b1-128">Use cualquiera de los métodos siguientes para iniciar la versión instalada de Windows PowerShell 3.0 o Windows PowerShell 4.0, según corresponda.</span><span class="sxs-lookup"><span data-stu-id="e37b1-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="e37b1-129">Desde el menú Inicio</span><span class="sxs-lookup"><span data-stu-id="e37b1-129">From the Start Menu</span></span>

- <span data-ttu-id="e37b1-130">Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="e37b1-131">Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="e37b1-132">En el símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="e37b1-132">At the Command Prompt</span></span>

<span data-ttu-id="e37b1-133">En **cmd.exe**, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e37b1-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="e37b1-134">También puede usar los parámetros del programa **powershell.exe** para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="e37b1-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="e37b1-135">Para obtener más información, consulte [Ayuda de línea de comandos de PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="e37b1-135">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="e37b1-136">Con privilegios administrativos (Ejecutar como administrador)</span><span class="sxs-lookup"><span data-stu-id="e37b1-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="e37b1-137">Haga clic en **Inicio**, escriba **PowerShell**, haga clic con el botón derecho en **Windows PowerShell** y, después, haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="e37b1-138">Iniciar Windows PowerShell ISE en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="e37b1-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="e37b1-139">Use cualquiera de los métodos siguientes para iniciar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e37b1-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="e37b1-140">Desde el menú Inicio</span><span class="sxs-lookup"><span data-stu-id="e37b1-140">From the Start Menu</span></span>

- <span data-ttu-id="e37b1-141">Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="e37b1-142">Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="e37b1-143">En el símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="e37b1-143">At the Command Prompt</span></span>

<span data-ttu-id="e37b1-144">En **cmd.exe**, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e37b1-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="e37b1-145">o</span><span class="sxs-lookup"><span data-stu-id="e37b1-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="e37b1-146">Con privilegios administrativos (Ejecutar como administrador)</span><span class="sxs-lookup"><span data-stu-id="e37b1-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="e37b1-147">Haga clic en **Inicio**, escriba **ISE**, haga clic con el botón derecho en **Windows PowerShell ISE** y, después, haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="e37b1-148">Habilitar Windows PowerShell ISE en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="e37b1-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="e37b1-149">En Windows PowerShell 4.0 y Windows PowerShell 3.0, Windows PowerShell ISE está habilitado de forma predeterminada en todas las versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="e37b1-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="e37b1-150">Si todavía no está habilitado, Windows Management Framework 4.0 o Windows Management Framework 3.0 lo habilitan.</span><span class="sxs-lookup"><span data-stu-id="e37b1-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="e37b1-151">En Windows PowerShell 2.0, Windows PowerShell ISE está habilitado de forma predeterminada en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e37b1-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="e37b1-152">Pero en Windows Server 2008 R2 y Windows Server 2008, es una característica opcional.</span><span class="sxs-lookup"><span data-stu-id="e37b1-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="e37b1-153">Para habilitar Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server 2008 R2 o Windows Server 2008, use el procedimiento siguiente.</span><span class="sxs-lookup"><span data-stu-id="e37b1-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="e37b1-154">Habilitar el Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e37b1-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="e37b1-155">Inicie el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="e37b1-155">Start Server Manager.</span></span>
2. <span data-ttu-id="e37b1-156">Haz clic en **Características** y, a continuación, en **Agregar características**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="e37b1-157">En Seleccionar características, haga clic en Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e37b1-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="e37b1-158">Iniciar la versión de 32 bits de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e37b1-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="e37b1-159">Al instalar Windows PowerShell en un equipo de 64 bits, **Windows PowerShell (x86)**, se instala una versión de 32 bits de Windows PowerShell además de la versión de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e37b1-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="e37b1-160">Al ejecutar Windows PowerShell, la versión de 64 bits se ejecuta de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="e37b1-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="e37b1-161">Pero en ocasiones tendrá que ejecutar **Windows PowerShell (x86)**, como cuando usa un módulo que requiere la versión de 32 bits o cuando se conecta de forma remota a un equipo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e37b1-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="e37b1-162">Para iniciar una versión de 32 bits de Windows PowerShell, use uno de los procedimientos siguientes.</span><span class="sxs-lookup"><span data-stu-id="e37b1-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="e37b1-163">En Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e37b1-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="e37b1-164">En la pantalla **Inicio**, escriba **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="e37b1-165">Haga clic en el icono **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="e37b1-166">En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-167">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-168">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e37b1-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="e37b1-169">En Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="e37b1-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="e37b1-170">En la página **Inicio**, escriba **Powershell** y, después, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-171">En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-172">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-173">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e37b1-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="e37b1-174">En Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="e37b1-174">In Windows® 8.1</span></span>

- <span data-ttu-id="e37b1-175">En la pantalla **Inicio**, escriba **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="e37b1-176">Haga clic en el icono **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="e37b1-177">Si ejecuta [Herramientas de administración remota del servidor](https://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, también puede abrir Windows PowerShell x86 desde el menú **Server ManagerTools** (Herramientas del administrador del servidor).</span><span class="sxs-lookup"><span data-stu-id="e37b1-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="e37b1-178">Seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-179">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-180">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e37b1-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="e37b1-181">En Windows® 8</span><span class="sxs-lookup"><span data-stu-id="e37b1-181">In Windows® 8</span></span>

- <span data-ttu-id="e37b1-182">En la pantalla **Inicio**, mueva el cursor a la esquina superior derecha, haga clic en **Configuración**, en **Mosaicos** y, después, mueva el control deslizante **Mostrar herramientas administrativas** a **Sí**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="e37b1-183">A continuación, escriba **PowerShell** y haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-184">Si ejecuta [Herramientas de administración remota del servidor](https://www.microsoft.com/download/details.aspx?id=28972) para Windows 8, también puede abrir Windows PowerShell x86 desde el menú **Server ManagerTools** (Herramientas del administrador del servidor).</span><span class="sxs-lookup"><span data-stu-id="e37b1-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="e37b1-185">Seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-186">En la página **Inicio** o en el escritorio, escriba **Powershell (x86)** y, después, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e37b1-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e37b1-187">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e37b1-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
