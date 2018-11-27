---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Requisitos del sistema de Windows PowerShell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 8850cf26b0313dfb8898ccb66b4767d695860d4c
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320744"
---
# <a name="windows-powershell-system-requirements"></a><span data-ttu-id="c7745-103">Requisitos del sistema de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7745-103">Windows PowerShell System Requirements</span></span>
<span data-ttu-id="c7745-104">En este tema se enumeran los requisitos del sistema de Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 y Windows PowerShell 5.1, así como de características especiales, como el Entorno de scripting integrado (ISE) de Windows PowerShell, los comandos CIM y los flujos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="c7745-104">This topic lists the system requirements for Windows PowerShell 3.0, Windows PowerShell 4.0 and Windows PowerShell 5.0, and Windows PowerShell 5.1 and for special features, such as Windows PowerShell Integrated Scripting Environment (ISE), CIM commands, and workflows.</span></span>

<span data-ttu-id="c7745-105">Windows® 8.1 y Windows Server® 2012 R2 incluyen todos los programas necesarios.</span><span class="sxs-lookup"><span data-stu-id="c7745-105">Windows® 8.1 and Windows Server® 2012 R2 include all required programs.</span></span> <span data-ttu-id="c7745-106">Este tema está diseñado para usuarios de versiones anteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="c7745-106">This topic is designed for users of earlier releases of Windows.</span></span>

## <a name="operating-system-requirements"></a><span data-ttu-id="c7745-107">Requisitos del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="c7745-107">Operating System Requirements</span></span>
<span data-ttu-id="c7745-108">Windows PowerShell 5.1 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="c7745-108">Windows PowerShell 5.1 runs on the following versions of Windows.</span></span>

- <span data-ttu-id="c7745-109">Windows Server 2019, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-109">Windows Server 2019, installed by default</span></span>

- <span data-ttu-id="c7745-110">Windows Server 2016, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-110">Windows Server 2016, installed by default</span></span>

- <span data-ttu-id="c7745-111">Windows Server 2012 R2: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c7745-111">Windows Server 2012 R2, install [Windows Management Framework 5.1](https://aka.ms/wmf5download) to run Windows PowerShell 5.1</span></span>

- <span data-ttu-id="c7745-112">Windows Server 2012: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7745-112">Windows Server 2012, install [Windows Management Framework 5.1](https://aka.ms/wmf5download) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="c7745-113">Windows Server 2008 R2 con Service Pack 1: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c7745-113">Windows Server 2008 R2 with Service Pack 1, install [Windows Management Framework 5.1](https://aka.ms/wmf5download) to run Windows PowerShell 5.1</span></span>

- <span data-ttu-id="c7745-114">Windows 10, versión 1607 y posteriores, instalado de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-114">Windows 10 version 1607 and up - installed by default</span></span>

- <span data-ttu-id="c7745-115">Windows 10, versiones 1507 y 1511: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c7745-115">Windows 10 version 1507, 1511 - install [Windows Management Framework 5.1](https://aka.ms/wmf5download) to run Windows PowerShell 5.1</span></span>

- <span data-ttu-id="c7745-116">Windows 8.1: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c7745-116">Windows 8.1, install [Windows Management Framework 5.1](https://aka.ms/wmf5download) to run Windows PowerShell 5.1</span></span>

- <span data-ttu-id="c7745-117">Windows 7 con Service Pack 1: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c7745-117">Windows 7 with Service Pack 1, install [Windows Management Framework 5.1](https://aka.ms/wmf5download) to run Windows PowerShell 5.1</span></span>

<span data-ttu-id="c7745-118">Windows PowerShell 5.0 (reemplazado por Windows PowerShell 5.1) se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="c7745-118">Windows PowerShell 5.0 (Superceeded by Windows PowerShell 5.1) runs on the following versions of Windows.</span></span>

- <span data-ttu-id="c7745-119">Windows Server 2019, versión posterior instalada de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-119">Windows Server 2019, higher version installed by default</span></span>

- <span data-ttu-id="c7745-120">Windows Server 2016, versión posterior instalada de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-120">Windows Server 2016, higher version installed by default</span></span>

- <span data-ttu-id="c7745-121">Windows Server 2012 R2: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7745-121">Windows Server 2012 R2, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="c7745-122">Windows Server 2012: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7745-122">Windows Server 2012, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="c7745-123">Windows Server 2008 R2 con Service Pack 1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7745-123">Windows Server 2008 R2 with Service Pack 1, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="c7745-124">Windows 10, versión 1607 y posteriores, versión posterior instalada de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-124">Windows 10 version 1607 and up - higher version installed by default</span></span>

- <span data-ttu-id="c7745-125">Windows 10, versiones 1507 y 1511, instalado de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-125">Windows 10 version 1507, 1511 - installed by default</span></span>

- <span data-ttu-id="c7745-126">Windows 8.1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7745-126">Windows 8.1, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

- <span data-ttu-id="c7745-127">Windows 7 con Service Pack 1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7745-127">Windows 7 with Service Pack 1, install [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) to run Windows PowerShell 5.0</span></span>

<span data-ttu-id="c7745-128">Windows PowerShell 4.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="c7745-128">Windows PowerShell 4.0 runs on the following versions of Windows.</span></span>

- <span data-ttu-id="c7745-129">Windows 8.1, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-129">Windows 8.1, installed by default</span></span>

- <span data-ttu-id="c7745-130">Windows Server 2012 R2, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-130">Windows Server 2012 R2, installed by default</span></span>

- <span data-ttu-id="c7745-131">Windows® 7 con Service Pack 1: instale [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para ejecutar Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="c7745-131">Windows® 7 with Service Pack 1, install [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) to run Windows PowerShell 4.0</span></span>

- <span data-ttu-id="c7745-132">Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para ejecutar Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="c7745-132">Windows Server® 2008 R2 with Service Pack 1, install [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) to run Windows PowerShell 4.0</span></span>

<span data-ttu-id="c7745-133">Windows PowerShell 3.0 se ejecuta en las siguientes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="c7745-133">Windows PowerShell 3.0 runs on the following versions of Windows.</span></span>

- <span data-ttu-id="c7745-134">Windows 8, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-134">Windows 8, installed by default</span></span>

- <span data-ttu-id="c7745-135">Windows Server 2012, instalado de manera predeterminada</span><span class="sxs-lookup"><span data-stu-id="c7745-135">Windows Server 2012, installed by default</span></span>

- <span data-ttu-id="c7745-136">Windows® 7 con Service Pack 1: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c7745-136">Windows® 7 with Service Pack 1, install [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

- <span data-ttu-id="c7745-137">Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c7745-137">Windows Server® 2008 R2 with Service Pack 1, install [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

- <span data-ttu-id="c7745-138">Windows Server 2008 con Service Pack 2: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c7745-138">Windows Server 2008 with Service Pack 2, install [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) to run Windows PowerShell 3.0</span></span>

## <a name="microsoft-net-framework-requirements"></a><span data-ttu-id="c7745-139">Requisitos de Microsoft .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7745-139">Microsoft .NET Framework Requirements</span></span>
<span data-ttu-id="c7745-140">Windows PowerShell 5.1 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c7745-140">Windows PowerShell 5.1 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="c7745-141">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="c7745-141">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="c7745-142">Windows PowerShell 5.0 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c7745-142">Windows PowerShell 5.0 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="c7745-143">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="c7745-143">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="c7745-144">Windows PowerShell 4.0 requiere la instalación completa de Microsoft .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c7745-144">Windows PowerShell 4.0 requires the full installation of Microsoft .NET Framework 4.5.</span></span> <span data-ttu-id="c7745-145">Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="c7745-145">Windows 8.1 and Windows Server 2012 R2 include Microsoft .NET Framework 4.5 by default.</span></span>

<span data-ttu-id="c7745-146">Windows PowerShell 3.0 requiere la instalación completa de Microsoft .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c7745-146">Windows PowerShell 3.0 requires the full installation of Microsoft .NET Framework 4.</span></span> <span data-ttu-id="c7745-147">Windows 8 y Windows Server 2012 incluyen Microsoft .NET Framework 4.5 de manera predeterminada, con lo que se cumple este requisito.</span><span class="sxs-lookup"><span data-stu-id="c7745-147">Windows 8 and Windows Server 2012 include Microsoft .NET Framework 4.5 by default, which fulfills this requirement.</span></span>

<span data-ttu-id="c7745-148">Para instalar Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), vea [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) en el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c7745-148">To install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), see [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) on the Microsoft Download Center.</span></span>

<span data-ttu-id="c7745-149">Para realizar la instalación completa de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), vea [Microsoft .NET Framework 4 (instalador web)](https://go.microsoft.com/fwlink/?LinkID=212931) en el Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c7745-149">To install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), see [Microsoft .NET Framework 4 (Web Installer)](https://go.microsoft.com/fwlink/?LinkID=212931) on the Microsoft Download Center.</span></span>

## <a name="windows-management-framework-40"></a><span data-ttu-id="c7745-150">Windows Management Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="c7745-150">Windows Management Framework 4.0</span></span>
<span data-ttu-id="c7745-151">Windows PowerShell 5.0 requiere que Windows Management Framework 4.0 esté preinstalado en Windows Server 2008 R2 SP1 y Windows 7 SP1.</span><span class="sxs-lookup"><span data-stu-id="c7745-151">Windows PowerShell 5.0 requires Windows Management Framework 4.0 to be preinstalled on Windows Server 2008 R2 SP1 and Windows 7 SP1.</span></span>

## <a name="ws-management-30"></a><span data-ttu-id="c7745-152">WS-Management 3.0</span><span class="sxs-lookup"><span data-stu-id="c7745-152">WS-Management 3.0</span></span>
<span data-ttu-id="c7745-153">Windows PowerShell 3.0 y Windows PowerShell 4.0 requieren WS-Management 3.0, que admite el servicio WinRM y el protocolo WSMan.</span><span class="sxs-lookup"><span data-stu-id="c7745-153">Windows PowerShell 3.0 and Windows PowerShell 4.0 require WS-Management 3.0, which supports the WinRM service and WSMan protocol.</span></span> <span data-ttu-id="c7745-154">Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="c7745-154">This program is included in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0, and Windows Management Framework 3.0.</span></span>

## <a name="windows-management-instrumentation-30"></a><span data-ttu-id="c7745-155">Instrumental de administración de Windows 3.0</span><span class="sxs-lookup"><span data-stu-id="c7745-155">Windows Management Instrumentation 3.0</span></span>
<span data-ttu-id="c7745-156">Windows PowerShell 3.0 y Windows PowerShell 4.0 requiere Instrumental de administración de Windows 3.0 (WMI).</span><span class="sxs-lookup"><span data-stu-id="c7745-156">Windows PowerShell 3.0 and Windows PowerShell 4.0 require Windows Management Instrumentation 3.0 (WMI).</span></span> <span data-ttu-id="c7745-157">Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="c7745-157">This program is included in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="c7745-158">Si este programa no está instalado en el equipo, las características que requieren WMI, como los comandos CIM, no se ejecutan.</span><span class="sxs-lookup"><span data-stu-id="c7745-158">If this program is not installed on the computer, features that require WMI, such as CIM commands, do not run.</span></span>

## <a name="common-language-runtime-40"></a><span data-ttu-id="c7745-159">Common Language Runtime 4.0</span><span class="sxs-lookup"><span data-stu-id="c7745-159">Common Language Runtime 4.0</span></span>
<span data-ttu-id="c7745-160">Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0 se compilan en Common Language Runtime (CLR) 4.0.</span><span class="sxs-lookup"><span data-stu-id="c7745-160">Windows PowerShell 3.0, Windows PowerShell 4.0, and Windows PowerShell 5.0 are compiled against Common Language Runtime (CLR) 4.0.</span></span>

## <a name="graphical-user-interface-requirements"></a><span data-ttu-id="c7745-161">Requisitos de la interfaz gráfica de usuario</span><span class="sxs-lookup"><span data-stu-id="c7745-161">Graphical User Interface Requirements</span></span>
<span data-ttu-id="c7745-162">Windows PowerShell es una aplicación basada en consola que no requiere una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="c7745-162">Windows PowerShell is a console-based application that does not require a graphical user interface.</span></span> <span data-ttu-id="c7745-163">Por lo tanto, es idónea para equipos que no tienen pantallas, monitores ni interfaz de usuario, como las opciones de instalación de Server Core de Windows Server 2012 R2 o Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="c7745-163">As such, is it well suited to computers that do not have screens or monitors, or a user interface, such as the Server Core installation options of Windows Server 2012 R2 or Windows Server 2012.</span></span>

<span data-ttu-id="c7745-164">Sin embargo, algunos elementos, como los siguientes, requieren una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="c7745-164">However, some items, such as the following, require a graphical user interface.</span></span> <span data-ttu-id="c7745-165">Para obtener más información, vea el tema de ayuda de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="c7745-165">For details, see the help topic for each item.</span></span>

- <span data-ttu-id="c7745-166">Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7745-166">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

- <span data-ttu-id="c7745-167">Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c7745-167">Cmdlets</span></span>

    1.  [<span data-ttu-id="c7745-168">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="c7745-168">Out-GridView</span></span>](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [<span data-ttu-id="c7745-169">Show-Command</span><span class="sxs-lookup"><span data-stu-id="c7745-169">Show-Command</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [<span data-ttu-id="c7745-170">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="c7745-170">Show-ControlPanelItem</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [<span data-ttu-id="c7745-171">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="c7745-171">Show-EventLog</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- <span data-ttu-id="c7745-172">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c7745-172">Parameters</span></span>

    1.  <span data-ttu-id="c7745-173">Parámetro **ShowWindow** del cmdlet [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="c7745-173">**ShowWindow** parameter of the [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span>

    2.  <span data-ttu-id="c7745-174">Parámetro **ShowSecurityDescriptorUI** de los cmdlets [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) y [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="c7745-174">**ShowSecurityDescriptorUI** parameter of the [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) and [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlets.</span></span>

## <a name="windows-powershell-engine-requirements"></a><span data-ttu-id="c7745-175">Requisitos del motor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7745-175">Windows PowerShell Engine Requirements</span></span>
<span data-ttu-id="c7745-176">Windows PowerShell 4.0 está diseñado para ser compatible con versiones anteriores de Windows PowerShell 3.0 y Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c7745-176">Windows PowerShell 4.0 is designed to be backwards compatible with Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="c7745-177">Los cmdlets, proveedores, complementos, módulos y scripts escritos para Windows PowerShell 2.0 y Windows PowerShell 3.0 se ejecutan sin cambios en Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c7745-177">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 and Windows PowerShell 3.0 run unchanged in Windows PowerShell 4.0.</span></span>

<span data-ttu-id="c7745-178">Sin embargo, debido a un cambio en la directiva de activación de tiempo de ejecución en Microsoft .NET Framework 4, los programas de host de Windows PowerShell escritos para Windows PowerShell 2.0 y compilados con Common Language Runtime (CLR) 2.0 no se pueden ejecutar sin modificaciones en versiones posteriores de Windows PowerShell 3.0, que está compilado con CLR 4.0.</span><span class="sxs-lookup"><span data-stu-id="c7745-178">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in Windows PowerShell 3.0, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="c7745-179">El motor de Windows PowerShell 2.0 requiere Microsoft .NET Framework 2.0.50727 como mínimo.</span><span class="sxs-lookup"><span data-stu-id="c7745-179">The Windows PowerShell 2.0 engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="c7745-180">Este requisito se cumple mediante Microsoft .NET Framework 3.5 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="c7745-180">This requirement is fulfilled by Microsoft .NET Framework 3.5 Service Pack 1.</span></span> <span data-ttu-id="c7745-181">Este requisito no se cumple con Microsoft .NET Framework 4 y versiones posteriores de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7745-181">This requirement is not fulfilled by Microsoft .NET Framework 4 and later releases of Microsoft .NET Framework.</span></span>

<span data-ttu-id="c7745-182">Para información sobre cómo agregar o instalar el motor de Windows PowerShell 2.0 y agregar o instalar las versiones necesarias de Microsoft .NET Framework, consulte [Instalación del motor de Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md).</span><span class="sxs-lookup"><span data-stu-id="c7745-182">For information about adding or installing the Windows PowerShell 2.0 engine, and adding or installing the required versions of the Microsoft .NET Framework, see [Installing the Windows PowerShell 2.0 Engine](Installing-the-Windows-PowerShell-2.0-Engine.md).</span></span> <span data-ttu-id="c7745-183">Para obtener información sobre cómo iniciar el motor de Windows PowerShell 2.0, consulte [Iniciar el motor de Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).</span><span class="sxs-lookup"><span data-stu-id="c7745-183">For information about starting the Windows PowerShell 2.0 engine, see [Starting the Windows PowerShell 2.0 Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="windows-preinstallation-environment"></a><span data-ttu-id="c7745-184">Entorno de preinstalación de Windows</span><span class="sxs-lookup"><span data-stu-id="c7745-184">Windows Preinstallation Environment</span></span>
<span data-ttu-id="c7745-185">Windows PowerShell 2.0, Windows PowerShell 3.0 y Windows PowerShell 4.0 se ejecutan en el Entorno de preinstalación de Windows (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="c7745-185">Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 run in the Windows Preinstallation Environment (Windows PE).</span></span> <span data-ttu-id="c7745-186">Sin embargo, no se admiten los siguientes cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c7745-186">However, the following cmdlets are not supported.</span></span>

- [<span data-ttu-id="c7745-187">Cmdlets del Servicio de transferencia inteligente en segundo plano (BITS)</span><span class="sxs-lookup"><span data-stu-id="c7745-187">Background Intelligent Transfer Service (BITS) Cmdlets</span></span>](https://go.microsoft.com/fwlink/?LinkId=257514)

- [<span data-ttu-id="c7745-188">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="c7745-188">Get-EventLog</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [<span data-ttu-id="c7745-189">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="c7745-189">Get-WinEvent</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [<span data-ttu-id="c7745-190">Save-Help</span><span class="sxs-lookup"><span data-stu-id="c7745-190">Save-Help</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [<span data-ttu-id="c7745-191">Update-Help</span><span class="sxs-lookup"><span data-stu-id="c7745-191">Update-Help</span></span>](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

<span data-ttu-id="c7745-192">Además, el servicio **WinRM** no está presente en Windows PE.</span><span class="sxs-lookup"><span data-stu-id="c7745-192">Also, the **WinRM** service is not present on Windows PE.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7745-193">Véase también</span><span class="sxs-lookup"><span data-stu-id="c7745-193">See Also</span></span>
- [<span data-ttu-id="c7745-194">Introducción a Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7745-194">Getting Started with Windows PowerShell</span></span>](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [<span data-ttu-id="c7745-195">Instalación de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7745-195">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- [<span data-ttu-id="c7745-196">Inicio de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7745-196">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
