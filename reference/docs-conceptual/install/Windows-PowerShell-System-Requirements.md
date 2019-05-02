---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Requisitos del sistema de Windows PowerShell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: a9a7dc434d26876d6747526ad3ef6fa598376ac1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058314"
---
# <a name="windows-powershell-system-requirements"></a>Requisitos del sistema de Windows PowerShell
En este tema se enumeran los requisitos del sistema de Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 y Windows PowerShell 5.1, así como de características especiales, como el Entorno de scripting integrado (ISE) de Windows PowerShell, los comandos CIM y los flujos de trabajo.

Windows® 8.1 y Windows Server® 2012 R2 incluyen todos los programas necesarios. Este tema está diseñado para usuarios de versiones anteriores de Windows.

## <a name="operating-system-requirements"></a>Requisitos del sistema operativo
Windows PowerShell 5.1 se ejecuta en las siguientes versiones de Windows.

- Windows Server 2019, instalado de manera predeterminada

- Windows Server 2016, instalado de manera predeterminada

- Windows Server 2012 R2: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1

- Windows Server 2012: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.0

- Windows Server 2008 R2 con Service Pack 1: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1

- Windows 10, versión 1607 y posteriores, instalado de forma predeterminada

- Windows 10, versiones 1507 y 1511: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1

- Windows 8.1: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1

- Windows 7 con Service Pack 1: instale [Windows Management Framework 5.1](https://aka.ms/wmf5download) para ejecutar Windows PowerShell 5.1

Windows PowerShell 5.0 (reemplazado por Windows PowerShell 5.1) se ejecuta en las siguientes versiones de Windows.

- Windows Server 2019, versión posterior instalada de forma predeterminada

- Windows Server 2016, versión posterior instalada de forma predeterminada

- Windows Server 2012 R2: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0

- Windows Server 2012: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0

- Windows Server 2008 R2 con Service Pack 1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0

- Windows 10, versión 1607 y posteriores, versión posterior instalada de forma predeterminada

- Windows 10, versiones 1507 y 1511, instalado de forma predeterminada

- Windows 8.1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0

- Windows 7 con Service Pack 1: instale [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para ejecutar Windows PowerShell 5.0

Windows PowerShell 4.0 se ejecuta en las siguientes versiones de Windows.

- Windows 8.1, instalado de manera predeterminada

- Windows Server 2012 R2, instalado de manera predeterminada

- Windows® 7 con Service Pack 1: instale [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para ejecutar Windows PowerShell 4.0

- Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para ejecutar Windows PowerShell 4.0

Windows PowerShell 3.0 se ejecuta en las siguientes versiones de Windows.

- Windows 8, instalado de manera predeterminada

- Windows Server 2012, instalado de manera predeterminada

- Windows® 7 con Service Pack 1: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0

- Windows Server® 2008 R2 con Service Pack 1: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0

- Windows Server 2008 con Service Pack 2: instale [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para ejecutar Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Requisitos de Microsoft .NET Framework
Windows PowerShell 5.1 requiere la instalación completa de Microsoft .NET Framework 4.5. Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.

Windows PowerShell 5.0 requiere la instalación completa de Microsoft .NET Framework 4.5. Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.

Windows PowerShell 4.0 requiere la instalación completa de Microsoft .NET Framework 4.5. Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada.

Windows PowerShell 3.0 requiere la instalación completa de Microsoft .NET Framework 4. Windows 8 y Windows Server 2012 incluyen Microsoft .NET Framework 4.5 de manera predeterminada, con lo que se cumple este requisito.

Para instalar Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), vea [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) en el Centro de descarga de Microsoft.

Para realizar la instalación completa de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), vea [Microsoft .NET Framework 4 (instalador web)](https://go.microsoft.com/fwlink/?LinkID=212931) en el Centro de descarga de Microsoft.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 requiere que Windows Management Framework 4.0 esté preinstalado en Windows Server 2008 R2 SP1 y Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 y Windows PowerShell 4.0 requieren WS-Management 3.0, que admite el servicio WinRM y el protocolo WSMan. Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Instrumental de administración de Windows 3.0
Windows PowerShell 3.0 y Windows PowerShell 4.0 requiere Instrumental de administración de Windows 3.0 (WMI). Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0. Si este programa no está instalado en el equipo, las características que requieren WMI, como los comandos CIM, no se ejecutan.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0 se compilan en Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Requisitos de la interfaz gráfica de usuario
Windows PowerShell es una aplicación basada en consola que no requiere una interfaz gráfica de usuario. Por lo tanto, es idónea para equipos que no tienen pantallas, monitores ni interfaz de usuario, como las opciones de instalación de Server Core de Windows Server 2012 R2 o Windows Server 2012.

Sin embargo, algunos elementos, como los siguientes, requieren una interfaz gráfica de usuario. Para obtener más información, vea el tema de ayuda de cada elemento.

- Entorno de scripting integrado (ISE) de Windows PowerShell

- Cmdlets

    1.  [Out-GridView](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Show-Command](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Show-ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Show-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parámetros

    1.  Parámetro **ShowWindow** del cmdlet [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help).

    2.  Parámetro **ShowSecurityDescriptorUI** de los cmdlets [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) y [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).

## <a name="windows-powershell-engine-requirements"></a>Requisitos del motor de Windows PowerShell
Windows PowerShell 4.0 está diseñado para ser compatible con versiones anteriores de Windows PowerShell 3.0 y Windows PowerShell 2.0. Los cmdlets, proveedores, complementos, módulos y scripts escritos para Windows PowerShell 2.0 y Windows PowerShell 3.0 se ejecutan sin cambios en Windows PowerShell 4.0.

Sin embargo, debido a un cambio en la directiva de activación de tiempo de ejecución en Microsoft .NET Framework 4, los programas de host de Windows PowerShell escritos para Windows PowerShell 2.0 y compilados con Common Language Runtime (CLR) 2.0 no se pueden ejecutar sin modificaciones en versiones posteriores de Windows PowerShell 3.0, que está compilado con CLR 4.0.

El motor de Windows PowerShell 2.0 requiere Microsoft .NET Framework 2.0.50727 como mínimo. Este requisito se cumple mediante Microsoft .NET Framework 3.5 Service Pack 1. Este requisito no se cumple con Microsoft .NET Framework 4 y versiones posteriores de Microsoft .NET Framework.

Para información sobre cómo agregar o instalar el motor de Windows PowerShell 2.0 y agregar o instalar las versiones necesarias de Microsoft .NET Framework, consulte [Instalación del motor de Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Para obtener información sobre cómo iniciar el motor de Windows PowerShell 2.0, consulte [Iniciar el motor de Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Entorno de preinstalación de Windows
Windows PowerShell 2.0, Windows PowerShell 3.0 y Windows PowerShell 4.0 se ejecutan en el Entorno de preinstalación de Windows (Windows PE). Sin embargo, no se admiten los siguientes cmdlets.

- [Cmdlets del Servicio de transferencia inteligente en segundo plano (BITS)](https://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Además, el servicio **WinRM** no está presente en Windows PE.

## <a name="see-also"></a>Véase también
- [Introducción a Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Instalación de Windows PowerShell](Installing-Windows-PowerShell.md)
- [Inicio de Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)
