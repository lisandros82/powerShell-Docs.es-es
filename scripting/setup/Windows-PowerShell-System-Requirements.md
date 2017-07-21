---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Requisitos del sistema de Windows PowerShell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 550d8adab18941da3204e0aea8fc8a70f890c289
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-system-requirements"></a><span data-ttu-id="a85dc-103">Requisitos del sistema de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a85dc-103">Windows PowerShell System Requirements</span></span>
<span data-ttu-id="a85dc-104">En este tema se enumeran los requisitos del sistema de Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0, así como de características especiales, como Entorno de scripting integrado (ISE) de Windows PowerShell, comandos CIM y flujos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a85dc-104">This topic lists the system requirements for Windows PowerShell 3.0, Windows PowerShell 4.0 and Windows PowerShell 5.0, and for special features, such as Windows PowerShell Integrated Scripting Environment (ISE), CIM commands, and workflows.</span></span>

<span data-ttu-id="a85dc-105">Windows® 8.1 y Windows Server® 2012 R2 incluyen todos los programas necesarios.</span><span class="sxs-lookup"><span data-stu-id="a85dc-105">Windows® 8.1 and Windows Server® 2012 R2 include all required programs.</span></span> <span data-ttu-id="a85dc-106">Este tema está diseñado para usuarios de versiones anteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="a85dc-106">This topic is designed for users of earlier releases of Windows.</span></span>

## <a name="operating-system-requirements"></a><span data-ttu-id="a85dc-107">Requisitos del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="a85dc-107">Operating System Requirements</span></span>
<span data-ttu-id="a85dc-108">Windows PowerShell 5.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="a85dc-108">Windows PowerShell 5.0 runs on the following versions of Windows.</span></span>

-   <span data-ttu-id="a85dc-109">Windows Server 2016, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="a85dc-109">Windows Server 2016, installed by default</span></span>

-   <span data-ttu-id="a85dc-110">Windows Server 2012 R2: instale [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-110">Windows Server 2012 R2, install [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) to run Windows PowerShell 5.0</span></span>

-   <span data-ttu-id="a85dc-111">Windows Server 2012: instale [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-111">Windows Server 2012, install [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) to run Windows PowerShell 5.0</span></span>

-   <span data-ttu-id="a85dc-112">Windows Server 2008 R2 con Service Pack 1: instale [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-112">Windows Server 2008 R2 with Service Pack 1, install [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) to run Windows PowerShell 5.0</span></span>

-   <span data-ttu-id="a85dc-113">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a85dc-113">Windows 8.1</span></span>

-   <span data-ttu-id="a85dc-114">Windows 7 con Service Pack 1: instale [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-114">Windows 7 with Service Pack 1, install [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkID=242919) to run Windows PowerShell 5.0</span></span>

<span data-ttu-id="a85dc-115">Windows PowerShell 4.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="a85dc-115">Windows PowerShell 4.0 runs on the following versions of Windows.</span></span>

-   <span data-ttu-id="a85dc-116">Windows 8.1, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="a85dc-116">Windows 8.1, installed by default</span></span>

-   <span data-ttu-id="a85dc-117">Windows Server 2012 R2, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="a85dc-117">Windows Server 2012 R2, installed by default</span></span>

-   <span data-ttu-id="a85dc-118">Windows® 7 con Service Pack 1: instale [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) para ejecutar Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-118">Windows® 7 with Service Pack 1, install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) to run Windows PowerShell 4.0</span></span>

-   <span data-ttu-id="a85dc-119">Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) para ejecutar Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-119">Windows Server® 2008 R2 with Service Pack 1, install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) to run Windows PowerShell 4.0</span></span>

<span data-ttu-id="a85dc-120">Windows PowerShell 3.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="a85dc-120">Windows PowerShell 3.0 runs on the following versions of Windows.</span></span>

-   <span data-ttu-id="a85dc-121">Windows 8, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="a85dc-121">Windows 8, installed by default</span></span>

-   <span data-ttu-id="a85dc-122">Windows Server 2012, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="a85dc-122">Windows Server 2012, installed by default</span></span>

-   <span data-ttu-id="a85dc-123">Windows® 7 con Service Pack 1: instale [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-123">Windows® 7 with Service Pack 1, install [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

-   <span data-ttu-id="a85dc-124">Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-124">Windows Server® 2008 R2 with Service Pack 1, install [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

-   <span data-ttu-id="a85dc-125">Windows Server 2008 con Service Pack 2: instale [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-125">Windows Server 2008 with Service Pack 2, install [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

## <a name="microsoft-net-framework-requirements"></a><span data-ttu-id="a85dc-126">Requisitos de Microsoft .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a85dc-126">Microsoft .NET Framework Requirements</span></span>
<span data-ttu-id="a85dc-127">Windows PowerShell 5.0 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a85dc-127">Windows PowerShell 5.0 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="a85dc-128">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a85dc-128">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="a85dc-129">Windows PowerShell 4.0 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a85dc-129">Windows PowerShell 4.0 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="a85dc-130">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a85dc-130">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="a85dc-131">Windows PowerShell 3.0 requiere la instalación completa de Microsoft .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a85dc-131">Windows PowerShell 3.0 requires the full installation of Microsoft .NET Framework 4.</span></span> <span data-ttu-id="a85dc-132">Windows 8 y Windows Server 2012 incluyen Microsoft .NET Framework 4.5 de manera predeterminada, con lo que se cumple este requisito.</span><span class="sxs-lookup"><span data-stu-id="a85dc-132">Windows 8 and Windows Server 2012 include Microsoft .NET Framework 4.5 by default, which fulfills this requirement.</span></span>

<span data-ttu-id="a85dc-133">Para instalar Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), vea [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) en el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a85dc-133">To install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), see [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) on the Microsoft Download Center.</span></span>

<span data-ttu-id="a85dc-134">Para realizar la instalación completa de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), vea [Microsoft .NET Framework 4 (instalador web)](http://go.microsoft.com/fwlink/?LinkID=212931) en el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a85dc-134">To install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), see [Microsoft .NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkID=212931) on the Microsoft Download Center.</span></span>

## <a name="windows-management-framework-40"></a><span data-ttu-id="a85dc-135">Windows Management Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-135">Windows Management Framework 4.0</span></span>
<span data-ttu-id="a85dc-136">Windows PowerShell 5.0 requiere que Windows Management Framework 4.0 esté preinstalado en Windows Server 2008 R2 SP1 y Windows 7 SP1.</span><span class="sxs-lookup"><span data-stu-id="a85dc-136">Windows PowerShell 5.0 requires Windows Management Framework 4.0 to be preinstalled on Windows Server 2008 R2 SP1 and Windows 7 SP1.</span></span>

## <a name="ws-management-30"></a><span data-ttu-id="a85dc-137">WS-Management 3.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-137">WS-Management 3.0</span></span>
<span data-ttu-id="a85dc-138">Windows PowerShell 3.0 y Windows PowerShell 4.0 requieren WS-Management 3.0, que admite el servicio WinRM y el protocolo WSMan.</span><span class="sxs-lookup"><span data-stu-id="a85dc-138">Windows PowerShell 3.0 and Windows PowerShell 4.0 require WS-Management 3.0, which supports the WinRM service and WSMan protocol.</span></span> <span data-ttu-id="a85dc-139">Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="a85dc-139">This program is included in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0, and Windows Management Framework 3.0.</span></span>

## <a name="windows-management-instrumentation-30"></a><span data-ttu-id="a85dc-140">Instrumental de administración de Windows 3.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-140">Windows Management Instrumentation 3.0</span></span>
<span data-ttu-id="a85dc-141">Windows PowerShell 3.0 y Windows PowerShell 4.0 requiere Instrumental de administración de Windows 3.0 (WMI).</span><span class="sxs-lookup"><span data-stu-id="a85dc-141">Windows PowerShell 3.0 and Windows PowerShell 4.0 require Windows Management Instrumentation 3.0 (WMI).</span></span> <span data-ttu-id="a85dc-142">Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="a85dc-142">This program is included in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="a85dc-143">Si este programa no está instalado en el equipo, las características que requieren WMI, como los comandos CIM, no se ejecutan.</span><span class="sxs-lookup"><span data-stu-id="a85dc-143">If this program is not installed on the computer, features that require WMI, such as CIM commands, do not run.</span></span>

## <a name="common-language-runtime-40"></a><span data-ttu-id="a85dc-144">Common Language Runtime 4.0</span><span class="sxs-lookup"><span data-stu-id="a85dc-144">Common Language Runtime 4.0</span></span>
<span data-ttu-id="a85dc-145">Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0 se compilan en Common Language Runtime (CLR) 4.0.</span><span class="sxs-lookup"><span data-stu-id="a85dc-145">Windows PowerShell 3.0, Windows PowerShell 4.0, and Windows PowerShell 5.0 are compiled against Common Language Runtime (CLR) 4.0.</span></span>

## <a name="graphical-user-interface-requirements"></a><span data-ttu-id="a85dc-146">Requisitos de la interfaz gráfica de usuario</span><span class="sxs-lookup"><span data-stu-id="a85dc-146">Graphical User Interface Requirements</span></span>
<span data-ttu-id="a85dc-147">Windows PowerShell es una aplicación basada en consola que no requiere una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="a85dc-147">Windows PowerShell is a console-based application that does not require a graphical user interface.</span></span> <span data-ttu-id="a85dc-148">Por lo tanto, es idónea para equipos que no tienen pantallas, monitores ni interfaz de usuario, como las opciones de instalación de Server Core de Windows Server 2012 R2 o Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="a85dc-148">As such, is it well suited to computers that do not have screens or monitors, or a user interface, such as the Server Core installation options of Windows Server 2012 R2 or Windows Server 2012.</span></span>

<span data-ttu-id="a85dc-149">Sin embargo, algunos elementos, como los siguientes, requieren una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="a85dc-149">However, some items, such as the following, require a graphical user interface.</span></span> <span data-ttu-id="a85dc-150">Para obtener más información, vea el tema de ayuda de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="a85dc-150">For details, see the help topic for each item.</span></span>

-   <span data-ttu-id="a85dc-151">Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a85dc-151">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

-   <span data-ttu-id="a85dc-152">Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a85dc-152">Cmdlets</span></span>

    1.  [<span data-ttu-id="a85dc-153">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="a85dc-153">Out-GridView</span></span>](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [<span data-ttu-id="a85dc-154">Show-Command</span><span class="sxs-lookup"><span data-stu-id="a85dc-154">Show-Command</span></span>](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [<span data-ttu-id="a85dc-155">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="a85dc-155">Show-ControlPanelItem</span></span>](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [<span data-ttu-id="a85dc-156">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="a85dc-156">Show-EventLog</span></span>](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   <span data-ttu-id="a85dc-157">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a85dc-157">Parameters</span></span>

    1.  <span data-ttu-id="a85dc-158">Parámetro **ShowWindow** del cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a).</span><span class="sxs-lookup"><span data-stu-id="a85dc-158">**ShowWindow** parameter of the [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet.</span></span>

    2.  <span data-ttu-id="a85dc-159">Parámetro **ShowSecurityDescriptorUI** de los cmdlets [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) y [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).</span><span class="sxs-lookup"><span data-stu-id="a85dc-159">**ShowSecurityDescriptorUI** parameter of the [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) and [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.</span></span>

## <a name="windows-powershell-engine-requirements"></a><span data-ttu-id="a85dc-160">Requisitos del motor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a85dc-160">Windows PowerShell Engine Requirements</span></span>
<span data-ttu-id="a85dc-161">Windows PowerShell 4.0 está diseñado para ser compatible con versiones anteriores de Windows PowerShell 3.0 y Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="a85dc-161">Windows PowerShell 4.0 is designed to be backwards compatible with Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="a85dc-162">Los cmdlets, proveedores, complementos, módulos y scripts escritos para Windows PowerShell 2.0 y Windows PowerShell 3.0 se ejecutan sin cambios en Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="a85dc-162">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 and Windows PowerShell 3.0 run unchanged in Windows PowerShell 4.0.</span></span>

<span data-ttu-id="a85dc-163">Sin embargo, debido a un cambio en la directiva de activación de tiempo de ejecución en Microsoft .NET Framework 4, los programas de host de Windows PowerShell escritos para Windows PowerShell 2.0 y compilados con Common Language Runtime (CLR) 2.0 no se pueden ejecutar sin modificaciones en versiones posteriores de Windows PowerShell 3.0, que está compilado con CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="a85dc-163">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in Windows PowerShell 3.0, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="a85dc-164">El motor de Windows PowerShell 2.0 requiere Microsoft .NET Framework 2.0.50727 como mínimo.</span><span class="sxs-lookup"><span data-stu-id="a85dc-164">The Windows PowerShell 2.0 engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="a85dc-165">Este requisito se cumple mediante Microsoft .NET Framework 3.5 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="a85dc-165">This requirement is fulfilled by Microsoft .NET Framework 3.5 Service Pack 1.</span></span> <span data-ttu-id="a85dc-166">Este requisito no se cumple con Microsoft .NET Framework 4 y versiones posteriores de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a85dc-166">This requirement is not fulfilled by Microsoft .NET Framework 4 and later releases of Microsoft .NET Framework.</span></span>

<span data-ttu-id="a85dc-167">Para información sobre cómo agregar o instalar el motor de Windows PowerShell 2.0 y agregar o instalar las versiones necesarias de Microsoft .NET Framework, consulte [Instalación del motor de Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md).</span><span class="sxs-lookup"><span data-stu-id="a85dc-167">For information about adding or installing the Windows PowerShell 2.0 engine, and adding or installing the required versions of the Microsoft .NET Framework, see [Installing the Windows PowerShell 2.0 Engine](Installing-the-Windows-PowerShell-2.0-Engine.md).</span></span> <span data-ttu-id="a85dc-168">Para obtener información sobre cómo iniciar el motor de Windows PowerShell 2.0, consulte [Iniciar el motor de Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).</span><span class="sxs-lookup"><span data-stu-id="a85dc-168">For information about starting the Windows PowerShell 2.0 engine, see [Starting the Windows PowerShell 2.0 Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="windows-preinstallation-environment"></a><span data-ttu-id="a85dc-169">Entorno de preinstalación de Windows</span><span class="sxs-lookup"><span data-stu-id="a85dc-169">Windows Preinstallation Environment</span></span>
<span data-ttu-id="a85dc-170">Windows PowerShell 2.0, Windows PowerShell 3.0 y Windows PowerShell 4.0 se ejecutan en el Entorno de preinstalación de Windows (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="a85dc-170">Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 run in the Windows Preinstallation Environment (Windows PE).</span></span> <span data-ttu-id="a85dc-171">Sin embargo, no se admiten los siguientes cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a85dc-171">However, the following cmdlets are not supported.</span></span>

-   [<span data-ttu-id="a85dc-172">Cmdlets del Servicio de transferencia inteligente en segundo plano (BITS)</span><span class="sxs-lookup"><span data-stu-id="a85dc-172">Background Intelligent Transfer Service (BITS) Cmdlets</span></span>](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [<span data-ttu-id="a85dc-173">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="a85dc-173">Get-EventLog</span></span>](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [<span data-ttu-id="a85dc-174">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="a85dc-174">Get-WinEvent</span></span>](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [<span data-ttu-id="a85dc-175">Save-Help</span><span class="sxs-lookup"><span data-stu-id="a85dc-175">Save-Help</span></span>](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [<span data-ttu-id="a85dc-176">Update-Help</span><span class="sxs-lookup"><span data-stu-id="a85dc-176">Update-Help</span></span>](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

<span data-ttu-id="a85dc-177">Además, el servicio **WinRM** no está presente en Windows PE.</span><span class="sxs-lookup"><span data-stu-id="a85dc-177">Also, the **WinRM** service is not present on Windows PE.</span></span>

## <a name="see-also"></a><span data-ttu-id="a85dc-178">Véase también</span><span class="sxs-lookup"><span data-stu-id="a85dc-178">See Also</span></span>
- [<span data-ttu-id="a85dc-179">Introducción a Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a85dc-179">Getting Started with Windows PowerShell</span></span>](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [<span data-ttu-id="a85dc-180">Instalación de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a85dc-180">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- [<span data-ttu-id="a85dc-181">Inicio de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a85dc-181">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

