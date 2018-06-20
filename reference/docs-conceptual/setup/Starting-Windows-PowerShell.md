---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Iniciar Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953130"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="327bd-103">Iniciar Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="327bd-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="327bd-104">PowerShell es una dll de motor de scripting que se inserta en varios hosts.</span><span class="sxs-lookup"><span data-stu-id="327bd-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="327bd-105">Los hosts más comunes que iniciará son la línea de comandos interactiva PowerShell.exe y el entorno de scripting interactivo PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="327bd-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="327bd-106">Para iniciar Windows PowerShell® en Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 y Windows 8, consulte [Navegación y tareas de administración comunes en Windows](http://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="327bd-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="327bd-107">Iniciar Windows PowerShell en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="327bd-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="327bd-108">En esta sección, se explica cómo iniciar Windows PowerShell y el Entorno de scripting integrado (ISE) de Windows PowerShell en Windows® 7, Windows Server® 2008 R2 y Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="327bd-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="327bd-109">También se explica cómo habilitar la característica opcional para Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server® 2008 R2 y Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="327bd-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="327bd-110">Use cualquiera de los métodos siguientes para iniciar la versión instalada de Windows PowerShell 3.0 o Windows PowerShell 4.0, según corresponda.</span><span class="sxs-lookup"><span data-stu-id="327bd-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="327bd-111">Desde el menú Inicio</span><span class="sxs-lookup"><span data-stu-id="327bd-111">From the Start Menu</span></span>

- <span data-ttu-id="327bd-112">Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="327bd-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="327bd-113">Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="327bd-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="327bd-114">En el símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="327bd-114">At the Command Prompt</span></span>

<span data-ttu-id="327bd-115">En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="327bd-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="327bd-116">También puede usar los parámetros del programa de PowerShell.exe para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="327bd-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="327bd-117">Para obtener más información, consulte [Ayuda de línea de comandos de PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="327bd-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="327bd-118">Con privilegios administrativos ("Ejecutar como administrador")</span><span class="sxs-lookup"><span data-stu-id="327bd-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="327bd-119">Haga clic en **Inicio**, escriba **PowerShell**, haga clic con el botón derecho en **Windows PowerShell** y, después, haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="327bd-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="327bd-120">Iniciar Windows PowerShell ISE en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="327bd-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="327bd-121">Use cualquiera de los métodos siguientes para iniciar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="327bd-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="327bd-122">Desde el menú Inicio</span><span class="sxs-lookup"><span data-stu-id="327bd-122">From the Start Menu</span></span>

- <span data-ttu-id="327bd-123">Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="327bd-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="327bd-124">Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="327bd-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="327bd-125">En el símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="327bd-125">At the Command Prompt</span></span>

<span data-ttu-id="327bd-126">En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="327bd-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="327bd-127">o</span><span class="sxs-lookup"><span data-stu-id="327bd-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="327bd-128">Con privilegios administrativos ("Ejecutar como administrador")</span><span class="sxs-lookup"><span data-stu-id="327bd-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="327bd-129">Haga clic en **Inicio**, escriba **ISE**, haga clic con el botón derecho en **Windows PowerShell ISE** y, después, haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="327bd-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="327bd-130">Habilitar Windows PowerShell ISE en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="327bd-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="327bd-131">En Windows PowerShell 4.0 y Windows PowerShell 3.0, Windows PowerShell ISE está habilitado de forma predeterminada en todas las versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="327bd-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="327bd-132">Si aún no está habilitado, Windows Management Framework 4.0 o Windows Management Framework 3.0 lo habilitan.</span><span class="sxs-lookup"><span data-stu-id="327bd-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="327bd-133">En Windows PowerShell 2.0, Windows PowerShell ISE está habilitado de forma predeterminada en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="327bd-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="327bd-134">Sin embargo, en Windows Server 2008 R2 y Windows Server 2008, es una característica opcional.</span><span class="sxs-lookup"><span data-stu-id="327bd-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="327bd-135">Para habilitar Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server 2008 R2 o Windows Server 2008, use el procedimiento siguiente.</span><span class="sxs-lookup"><span data-stu-id="327bd-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="327bd-136">Habilitar el Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="327bd-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="327bd-137">Inicie el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="327bd-137">Start Server Manager.</span></span>
2. <span data-ttu-id="327bd-138">Haz clic en **Características** y, a continuación, en **Agregar características**.</span><span class="sxs-lookup"><span data-stu-id="327bd-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="327bd-139">En Seleccionar características, haga clic en Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="327bd-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="327bd-140">Iniciar la versión de 32 bits de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="327bd-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="327bd-141">Al instalar Windows PowerShell en un equipo de 64 bits, **Windows PowerShell (x86)**, se instala una versión de 32 bits de Windows PowerShell además de la versión de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="327bd-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="327bd-142">Al ejecutar Windows PowerShell, la versión de 64 bits se ejecuta de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="327bd-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="327bd-143">Sin embargo, en ocasiones deberá ejecutar **Windows PowerShell (x86)**, como cuando usa un módulo que requiere la versión 32 bits o cuando se conecta de forma remota a un equipo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="327bd-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="327bd-144">Para iniciar una versión de 32 bits de Windows PowerShell, use uno de los procedimientos siguientes.</span><span class="sxs-lookup"><span data-stu-id="327bd-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="327bd-145">En Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="327bd-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="327bd-146">En la pantalla **Inicio**, escriba **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="327bd-147">Haga clic en el icono **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="327bd-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="327bd-148">En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-149">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-150">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="327bd-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="327bd-151">En Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="327bd-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="327bd-152">En la página **Inicio**, escriba **Powershell** y, después, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-153">En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-154">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-155">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="327bd-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="327bd-156">En Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="327bd-156">In Windows® 8.1</span></span>

- <span data-ttu-id="327bd-157">En la pantalla **Inicio**, escriba **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="327bd-158">Haga clic en el icono **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="327bd-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="327bd-159">Si está ejecutando [Herramientas de administración remota del servidor](http://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, también puede abrir Windows PowerShell x86 desde el menú **Server Manager Tools** (Herramientas del administrador del servidor).</span><span class="sxs-lookup"><span data-stu-id="327bd-159">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="327bd-160">Seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-161">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-162">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="327bd-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="327bd-163">En Windows® 8</span><span class="sxs-lookup"><span data-stu-id="327bd-163">In Windows® 8</span></span>

- <span data-ttu-id="327bd-164">En la pantalla **Inicio**, mueva el cursor a la esquina superior derecha, haga clic en **Configuración**, haga clic en **Mosaicos** y, a continuación, mueva el control deslizante **Mostrar herramientas administrativas** a Sí.</span><span class="sxs-lookup"><span data-stu-id="327bd-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="327bd-165">A continuación, escriba **PowerShell** y haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-166">Si está ejecutando [Herramientas de administración remota del servidor](http://www.microsoft.com/download/details.aspx?id=28972) para Windows 8, también puede abrir Windows PowerShell x86 desde el menú **Server ManagerTools** (Herramientas del administrador del servidor).</span><span class="sxs-lookup"><span data-stu-id="327bd-166">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="327bd-167">Seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-168">En la página **Inicio** o en el escritorio, escriba **Powershell (x86)** y, después, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="327bd-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="327bd-169">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="327bd-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>