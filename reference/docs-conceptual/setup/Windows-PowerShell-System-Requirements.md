---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Requisitos del sistema de Windows PowerShell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 33824eac4de28de97990ffa1ea2500e61e03e847
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2017
---
# <a name="windows-powershell-system-requirements"></a><span data-ttu-id="66b37-103">Requisitos del sistema de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b37-103">Windows PowerShell System Requirements</span></span>
<span data-ttu-id="66b37-104">En este tema se enumeran los requisitos del sistema de Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0, así como de características especiales, como Entorno de scripting integrado (ISE) de Windows PowerShell, comandos CIM y flujos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="66b37-104">This topic lists the system requirements for Windows PowerShell 3.0, Windows PowerShell 4.0 and Windows PowerShell 5.0, and for special features, such as Windows PowerShell Integrated Scripting Environment (ISE), CIM commands, and workflows.</span></span>

<span data-ttu-id="66b37-105">Windows® 8.1 y Windows Server® 2012 R2 incluyen todos los programas necesarios.</span><span class="sxs-lookup"><span data-stu-id="66b37-105">Windows® 8.1 and Windows Server® 2012 R2 include all required programs.</span></span> <span data-ttu-id="66b37-106">Este tema está diseñado para usuarios de versiones anteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="66b37-106">This topic is designed for users of earlier releases of Windows.</span></span>

## <a name="operating-system-requirements"></a><span data-ttu-id="66b37-107">Requisitos del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="66b37-107">Operating System Requirements</span></span>
<span data-ttu-id="66b37-108">Windows PowerShell 5.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="66b37-108">Windows PowerShell 5.0 runs on the following versions of Windows.</span></span>

- <span data-ttu-id="66b37-109">Windows Server 2016, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="66b37-109">Windows Server 2016, installed by default</span></span>

- <span data-ttu-id="66b37-110">Windows Server 2012 R2: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="66b37-110">Windows Server 2012 R2, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="66b37-111">Windows Server 2012: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="66b37-111">Windows Server 2012, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="66b37-112">Windows Server 2008 R2 con Service Pack 1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="66b37-112">Windows Server 2008 R2 with Service Pack 1, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="66b37-113">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="66b37-113">Windows 8.1</span></span>

- <span data-ttu-id="66b37-114">Windows 7 con Service Pack 1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="66b37-114">Windows 7 with Service Pack 1, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

<span data-ttu-id="66b37-115">Windows PowerShell 4.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="66b37-115">Windows PowerShell 4.0 runs on the following versions of Windows.</span></span>

- <span data-ttu-id="66b37-116">Windows 8.1, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="66b37-116">Windows 8.1, installed by default</span></span>

- <span data-ttu-id="66b37-117">Windows Server 2012 R2, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="66b37-117">Windows Server 2012 R2, installed by default</span></span>

- <span data-ttu-id="66b37-118">Windows® 7 con Service Pack 1: instale [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para ejecutar Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="66b37-118">Windows® 7 with Service Pack 1, install [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) to run Windows PowerShell 4.0</span></span>

- <span data-ttu-id="66b37-119">Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para ejecutar Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="66b37-119">Windows Server® 2008 R2 with Service Pack 1, install [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) to run Windows PowerShell 4.0</span></span>

<span data-ttu-id="66b37-120">Windows PowerShell 3.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="66b37-120">Windows PowerShell 3.0 runs on the following versions of Windows.</span></span>

- <span data-ttu-id="66b37-121">Windows 8, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="66b37-121">Windows 8, installed by default</span></span>

- <span data-ttu-id="66b37-122">Windows Server 2012, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="66b37-122">Windows Server 2012, installed by default</span></span>

- <span data-ttu-id="66b37-123">Windows® 7 con Service Pack 1: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="66b37-123">Windows® 7 with Service Pack 1, install [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

- <span data-ttu-id="66b37-124">Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="66b37-124">Windows Server® 2008 R2 with Service Pack 1, install [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

- <span data-ttu-id="66b37-125">Windows Server 2008 con Service Pack 2: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="66b37-125">Windows Server 2008 with Service Pack 2, install [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

## <a name="microsoft-net-framework-requirements"></a><span data-ttu-id="66b37-126">Requisitos de Microsoft .NET Framework</span><span class="sxs-lookup"><span data-stu-id="66b37-126">Microsoft .NET Framework Requirements</span></span>
<span data-ttu-id="66b37-127">Windows PowerShell 5.0 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="66b37-127">Windows PowerShell 5.0 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="66b37-128">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="66b37-128">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="66b37-129">Windows PowerShell 4.0 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="66b37-129">Windows PowerShell 4.0 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="66b37-130">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="66b37-130">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="66b37-131">Windows PowerShell 3.0 requiere la instalación completa de Microsoft .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="66b37-131">Windows PowerShell 3.0 requires the full installation of Microsoft .NET Framework 4.</span></span> <span data-ttu-id="66b37-132">Windows 8 y Windows Server 2012 incluyen Microsoft .NET Framework 4.5 de manera predeterminada, con lo que se cumple este requisito.</span><span class="sxs-lookup"><span data-stu-id="66b37-132">Windows 8 and Windows Server 2012 include Microsoft .NET Framework 4.5 by default, which fulfills this requirement.</span></span>

<span data-ttu-id="66b37-133">Para instalar Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), vea [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) en el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="66b37-133">To install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), see [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) on the Microsoft Download Center.</span></span>

<span data-ttu-id="66b37-134">Para realizar la instalación completa de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), vea [Microsoft .NET Framework 4 (instalador web)](http://go.microsoft.com/fwlink/?LinkID=212931) en el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="66b37-134">To install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), see [Microsoft .NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkID=212931) on the Microsoft Download Center.</span></span>

## <a name="windows-management-framework-40"></a><span data-ttu-id="66b37-135">Windows Management Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="66b37-135">Windows Management Framework 4.0</span></span>
<span data-ttu-id="66b37-136">Windows PowerShell 5.0 requiere que Windows Management Framework 4.0 esté preinstalado en Windows Server 2008 R2 SP1 y Windows 7 SP1.</span><span class="sxs-lookup"><span data-stu-id="66b37-136">Windows PowerShell 5.0 requires Windows Management Framework 4.0 to be preinstalled on Windows Server 2008 R2 SP1 and Windows 7 SP1.</span></span>

## <a name="ws-management-30"></a><span data-ttu-id="66b37-137">WS-Management 3.0</span><span class="sxs-lookup"><span data-stu-id="66b37-137">WS-Management 3.0</span></span>
<span data-ttu-id="66b37-138">Windows PowerShell 3.0 y Windows PowerShell 4.0 requieren WS-Management 3.0, que admite el servicio WinRM y el protocolo WSMan.</span><span class="sxs-lookup"><span data-stu-id="66b37-138">Windows PowerShell 3.0 and Windows PowerShell 4.0 require WS-Management 3.0, which supports the WinRM service and WSMan protocol.</span></span> <span data-ttu-id="66b37-139">Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="66b37-139">This program is included in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0, and Windows Management Framework 3.0.</span></span>

## <a name="windows-management-instrumentation-30"></a><span data-ttu-id="66b37-140">Instrumental de administración de Windows 3.0</span><span class="sxs-lookup"><span data-stu-id="66b37-140">Windows Management Instrumentation 3.0</span></span>
<span data-ttu-id="66b37-141">Windows PowerShell 3.0 y Windows PowerShell 4.0 requiere Instrumental de administración de Windows 3.0 (WMI).</span><span class="sxs-lookup"><span data-stu-id="66b37-141">Windows PowerShell 3.0 and Windows PowerShell 4.0 require Windows Management Instrumentation 3.0 (WMI).</span></span> <span data-ttu-id="66b37-142">Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="66b37-142">This program is included in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="66b37-143">Si este programa no está instalado en el equipo, las características que requieren WMI, como los comandos CIM, no se ejecutan.</span><span class="sxs-lookup"><span data-stu-id="66b37-143">If this program is not installed on the computer, features that require WMI, such as CIM commands, do not run.</span></span>

## <a name="common-language-runtime-40"></a><span data-ttu-id="66b37-144">Common Language Runtime 4.0</span><span class="sxs-lookup"><span data-stu-id="66b37-144">Common Language Runtime 4.0</span></span>
<span data-ttu-id="66b37-145">Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0 se compilan en Common Language Runtime (CLR) 4.0.</span><span class="sxs-lookup"><span data-stu-id="66b37-145">Windows PowerShell 3.0, Windows PowerShell 4.0, and Windows PowerShell 5.0 are compiled against Common Language Runtime (CLR) 4.0.</span></span>

## <a name="graphical-user-interface-requirements"></a><span data-ttu-id="66b37-146">Requisitos de la interfaz gráfica de usuario</span><span class="sxs-lookup"><span data-stu-id="66b37-146">Graphical User Interface Requirements</span></span>
<span data-ttu-id="66b37-147">Windows PowerShell es una aplicación basada en consola que no requiere una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="66b37-147">Windows PowerShell is a console-based application that does not require a graphical user interface.</span></span> <span data-ttu-id="66b37-148">Por lo tanto, es idónea para equipos que no tienen pantallas, monitores ni interfaz de usuario, como las opciones de instalación de Server Core de Windows Server 2012 R2 o Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="66b37-148">As such, is it well suited to computers that do not have screens or monitors, or a user interface, such as the Server Core installation options of Windows Server 2012 R2 or Windows Server 2012.</span></span>

<span data-ttu-id="66b37-149">Sin embargo, algunos elementos, como los siguientes, requieren una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="66b37-149">However, some items, such as the following, require a graphical user interface.</span></span> <span data-ttu-id="66b37-150">Para obtener más información, vea el tema de ayuda de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="66b37-150">For details, see the help topic for each item.</span></span>

- <span data-ttu-id="66b37-151">Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b37-151">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

- <span data-ttu-id="66b37-152">Cmdlets</span><span class="sxs-lookup"><span data-stu-id="66b37-152">Cmdlets</span></span>

    1.  [<span data-ttu-id="66b37-153">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="66b37-153">Out-GridView</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [<span data-ttu-id="66b37-154">Show-Command</span><span class="sxs-lookup"><span data-stu-id="66b37-154">Show-Command</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [<span data-ttu-id="66b37-155">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="66b37-155">Show-ControlPanelItem</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [<span data-ttu-id="66b37-156">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="66b37-156">Show-EventLog</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- <span data-ttu-id="66b37-157">Parámetros</span><span class="sxs-lookup"><span data-stu-id="66b37-157">Parameters</span></span>

    1.  <span data-ttu-id="66b37-158">Parámetro **ShowWindow** del cmdlet [Get-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="66b37-158">**ShowWindow** parameter of the [Get-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span>

    2.  <span data-ttu-id="66b37-159">Parámetro **ShowSecurityDescriptorUI** de los cmdlets [Register-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) y [Set-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="66b37-159">**ShowSecurityDescriptorUI** parameter of the [Register-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) and [Set-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlets.</span></span>

## <a name="windows-powershell-engine-requirements"></a><span data-ttu-id="66b37-160">Requisitos del motor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b37-160">Windows PowerShell Engine Requirements</span></span>
<span data-ttu-id="66b37-161">Windows PowerShell 4.0 está diseñado para ser compatible con versiones anteriores de Windows PowerShell 3.0 y Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="66b37-161">Windows PowerShell 4.0 is designed to be backwards compatible with Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="66b37-162">Los cmdlets, proveedores, complementos, módulos y scripts escritos para Windows PowerShell 2.0 y Windows PowerShell 3.0 se ejecutan sin cambios en Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="66b37-162">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 and Windows PowerShell 3.0 run unchanged in Windows PowerShell 4.0.</span></span>

<span data-ttu-id="66b37-163">Sin embargo, debido a un cambio en la directiva de activación de tiempo de ejecución en Microsoft .NET Framework 4, los programas de host de Windows PowerShell escritos para Windows PowerShell 2.0 y compilados con Common Language Runtime (CLR) 2.0 no se pueden ejecutar sin modificaciones en versiones posteriores de Windows PowerShell 3.0, que está compilado con CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="66b37-163">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in Windows PowerShell 3.0, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="66b37-164">El motor de Windows PowerShell 2.0 requiere Microsoft .NET Framework 2.0.50727 como mínimo.</span><span class="sxs-lookup"><span data-stu-id="66b37-164">The Windows PowerShell 2.0 engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="66b37-165">Este requisito se cumple mediante Microsoft .NET Framework 3.5 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="66b37-165">This requirement is fulfilled by Microsoft .NET Framework 3.5 Service Pack 1.</span></span> <span data-ttu-id="66b37-166">Este requisito no se cumple con Microsoft .NET Framework 4 y versiones posteriores de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66b37-166">This requirement is not fulfilled by Microsoft .NET Framework 4 and later releases of Microsoft .NET Framework.</span></span>

<span data-ttu-id="66b37-167">Para información sobre cómo agregar o instalar el motor de Windows PowerShell 2.0 y agregar o instalar las versiones necesarias de Microsoft .NET Framework, consulte [Instalación del motor de Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md).</span><span class="sxs-lookup"><span data-stu-id="66b37-167">For information about adding or installing the Windows PowerShell 2.0 engine, and adding or installing the required versions of the Microsoft .NET Framework, see [Installing the Windows PowerShell 2.0 Engine](Installing-the-Windows-PowerShell-2.0-Engine.md).</span></span> <span data-ttu-id="66b37-168">Para obtener información sobre cómo iniciar el motor de Windows PowerShell 2.0, consulte [Iniciar el motor de Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).</span><span class="sxs-lookup"><span data-stu-id="66b37-168">For information about starting the Windows PowerShell 2.0 engine, see [Starting the Windows PowerShell 2.0 Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="windows-preinstallation-environment"></a><span data-ttu-id="66b37-169">Entorno de preinstalación de Windows</span><span class="sxs-lookup"><span data-stu-id="66b37-169">Windows Preinstallation Environment</span></span>
<span data-ttu-id="66b37-170">Windows PowerShell 2.0, Windows PowerShell 3.0 y Windows PowerShell 4.0 se ejecutan en el Entorno de preinstalación de Windows (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="66b37-170">Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 run in the Windows Preinstallation Environment (Windows PE).</span></span> <span data-ttu-id="66b37-171">Sin embargo, no se admiten los siguientes cmdlets.</span><span class="sxs-lookup"><span data-stu-id="66b37-171">However, the following cmdlets are not supported.</span></span>

- [<span data-ttu-id="66b37-172">Cmdlets del Servicio de transferencia inteligente en segundo plano (BITS)</span><span class="sxs-lookup"><span data-stu-id="66b37-172">Background Intelligent Transfer Service (BITS) Cmdlets</span></span>](http://go.microsoft.com/fwlink/?LinkId=257514)

- [<span data-ttu-id="66b37-173">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="66b37-173">Get-EventLog</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [<span data-ttu-id="66b37-174">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="66b37-174">Get-WinEvent</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [<span data-ttu-id="66b37-175">Save-Help</span><span class="sxs-lookup"><span data-stu-id="66b37-175">Save-Help</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [<span data-ttu-id="66b37-176">Update-Help</span><span class="sxs-lookup"><span data-stu-id="66b37-176">Update-Help</span></span>](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Update-Help)

<span data-ttu-id="66b37-177">Además, el servicio **WinRM** no está presente en Windows PE.</span><span class="sxs-lookup"><span data-stu-id="66b37-177">Also, the **WinRM** service is not present on Windows PE.</span></span>

## <a name="see-also"></a><span data-ttu-id="66b37-178">Véase también</span><span class="sxs-lookup"><span data-stu-id="66b37-178">See Also</span></span>
- [<span data-ttu-id="66b37-179">Introducción a Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b37-179">Getting Started with Windows PowerShell</span></span>](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [<span data-ttu-id="66b37-180">Instalación de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b37-180">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- [<span data-ttu-id="66b37-181">Inicio de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66b37-181">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)

