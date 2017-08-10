---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Iniciar Windows PowerShell en versiones anteriores de Windows
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="27093-103">Iniciar Windows PowerShell en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="27093-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="27093-104">En esta sección, se explica cómo iniciar Windows PowerShell y el Entorno de scripting integrado (ISE) de Windows PowerShell en Windows® 7, Windows Server® 2008 R2 y Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="27093-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="27093-105">También se explica cómo habilitar la característica opcional para Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server® 2008 R2 y Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="27093-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="27093-106">Para instalar Windows PowerShell 4.0 en sistemas compatibles, descargue e instale [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="27093-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="27093-107">Para obtener más información, consulte [Instalar Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="27093-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="27093-108">Para instalar Windows PowerShell 3.0 en sistemas compatibles, descargue e instale [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="27093-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="27093-109">Para obtener más información, consulte [Instalar Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="27093-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="27093-110">Iniciar Windows PowerShell en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="27093-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="27093-111">Use cualquiera de los métodos siguientes para iniciar la versión instalada de Windows PowerShell 3.0 o Windows PowerShell 4.0, según corresponda.</span><span class="sxs-lookup"><span data-stu-id="27093-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="27093-112">Desde el menú Inicio</span><span class="sxs-lookup"><span data-stu-id="27093-112">From the Start Menu</span></span>

-   <span data-ttu-id="27093-113">Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="27093-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

-   <span data-ttu-id="27093-114">Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="27093-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="27093-115">En el símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="27093-115">At the Command Prompt</span></span>

-   <span data-ttu-id="27093-116">En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="27093-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="27093-117">También puede usar los parámetros del programa de PowerShell.exe para personalizar la sesión.</span><span class="sxs-lookup"><span data-stu-id="27093-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="27093-118">Para obtener más información, consulte [Ayuda de línea de comandos de PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="27093-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="27093-119">Con privilegios administrativos ("Ejecutar como administrador")</span><span class="sxs-lookup"><span data-stu-id="27093-119">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="27093-120">Haga clic en **Inicio**, escriba **PowerShell**, haga clic con el botón derecho en **Windows PowerShell** y, después, haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="27093-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="27093-121">Iniciar Windows PowerShell ISE en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="27093-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="27093-122">Use cualquiera de los métodos siguientes para iniciar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="27093-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="27093-123">Desde el menú Inicio</span><span class="sxs-lookup"><span data-stu-id="27093-123">From the Start Menu</span></span>

-   <span data-ttu-id="27093-124">Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="27093-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

-   <span data-ttu-id="27093-125">Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="27093-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="27093-126">En el símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="27093-126">At the Command Prompt</span></span>

-   <span data-ttu-id="27093-127">En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:</span><span class="sxs-lookup"><span data-stu-id="27093-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="27093-128">o</span><span class="sxs-lookup"><span data-stu-id="27093-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="27093-129">Con privilegios administrativos ("Ejecutar como administrador")</span><span class="sxs-lookup"><span data-stu-id="27093-129">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="27093-130">Haga clic en **Inicio**, escriba **ISE**, haga clic con el botón derecho en **Windows PowerShell ISE** y, después, haga clic en **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="27093-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="27093-131">Habilitar Windows PowerShell ISE en versiones anteriores de Windows</span><span class="sxs-lookup"><span data-stu-id="27093-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="27093-132">En Windows PowerShell 4.0 y Windows PowerShell 3.0, Windows PowerShell ISE está habilitado de forma predeterminada en todas las versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="27093-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="27093-133">Si aún no está habilitado, Windows Management Framework 4.0 o Windows Management Framework 3.0 lo habilitan.</span><span class="sxs-lookup"><span data-stu-id="27093-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="27093-134">En Windows PowerShell 2.0, Windows PowerShell ISE está habilitado de forma predeterminada en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="27093-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="27093-135">Sin embargo, en Windows Server 2008 R2 y Windows Server 2008, es una característica opcional.</span><span class="sxs-lookup"><span data-stu-id="27093-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="27093-136">Para habilitar Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server 2008 R2 o Windows Server 2008, use el procedimiento siguiente.</span><span class="sxs-lookup"><span data-stu-id="27093-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="27093-137">Habilitar el Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="27093-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1.  <span data-ttu-id="27093-138">Inicie el Administrador del servidor.</span><span class="sxs-lookup"><span data-stu-id="27093-138">Start Server Manager.</span></span>

2.  <span data-ttu-id="27093-139">Haz clic en **Características** y, a continuación, en **Agregar características**.</span><span class="sxs-lookup"><span data-stu-id="27093-139">Click **Features** and then click **Add Features**.</span></span>

3.  <span data-ttu-id="27093-140">En Seleccionar características, haga clic en Entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27093-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

