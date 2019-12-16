---
ms.date: 12/06/2019
keywords: powershell, cmdlet
title: Requisitos del sistema de Windows PowerShell
ms.openlocfilehash: 713b062916fec0c5c70ea9a7f95fea3570afb64a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953796"
---
# <a name="windows-powershell-system-requirements"></a>Requisitos del sistema de Windows PowerShell

En este artículo se enumeran los requisitos del sistema para Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 y Windows PowerShell 5.1. Y, características especiales, como el entorno de scripting integrado (ISE) de Windows PowerShell, los comandos del Modelo de información común (CIM) y los flujos de trabajo.

Windows® 8.1 y Windows Server® 2012 R2 incluyen todos los programas necesarios. Este artículo está diseñado para usuarios de versiones anteriores de Windows.

## <a name="operating-system-requirements"></a>Requisitos de sistema operativo

### <a name="windows-powershell-51"></a>Windows PowerShell 5.1

Windows PowerShell 5.1 se ejecuta en las siguientes versiones de Windows. Para ejecutar Windows PowerShell 5.1, instale Windows Management Framework 5.1. Para más información, consulte [Instalación y configuración de WMF 5.1](../wmf/setup/install-configure.md).

| Versión de Windows | Requisito del sistema |
| ----- | ----- |
| Windows Server 2019 | Instalado de forma predeterminada |
| Windows Server 2016 | Instalado de forma predeterminada |
| Windows Server 2012 R2 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 con Service Pack 1 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 versión 1607 y posteriores | Instalado de forma predeterminada |
| Windows 10 versión 1507, 1511 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 8.1 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 con Service Pack 1 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows PowerShell 5.0 se ejecuta en las siguientes versiones de Windows. Para ejecutar Windows PowerShell 5.0, instale Windows Management Framework 5.1. Para más información, consulte [Instalación y configuración de WMF 5.1](../wmf/setup/install-configure.md). Windows Management Framework 5.1 sustituye a Windows Management Framework 5.0.

| Versión de Windows | Requisito del sistema |
| ----- | ----- |
| Windows Server 2019 | Versión posterior instalada de forma predeterminada |
| Windows Server 2016 | Versión posterior instalada de forma predeterminada |
| Windows Server 2012 R2 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 con Service Pack 1 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 versión 1607 y posteriores | Versión posterior instalada de forma predeterminada |
| Windows 10 versión 1507, 1511 | Instalado de forma predeterminada |
| Windows 8.1 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 con Service Pack 1 | Instalar [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows PowerShell 4.0 se ejecuta en las siguientes versiones de Windows. Para ejecutar Windows PowerShell 4.0, instale la versión especificada de Windows Management Framework para el sistema operativo.

| Versión de Windows | Requisito del sistema |
| ----- | ----- |
| Windows 8.1 | Instalado de forma predeterminada |
| Windows Server 2012 R2 | Instalado de forma predeterminada |
| Windows® 7 con Service Pack 1 | Instalar [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 con Service Pack 1 | Instalar [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows PowerShell 3.0 se ejecuta en las siguientes versiones de Windows. Para ejecutar Windows PowerShell 3.0, instale la versión especificada de Windows Management Framework para su sistema operativo.

| Versión de Windows | Requisito del sistema |
| ----- | ----- |
| Windows 8 | Instalado de forma predeterminada |
| Windows Server 2012 | Instalado de forma predeterminada |
| Windows® 7 con Service Pack 1 | Instalar [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 con Service Pack 1 | Instalar [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server 2008 con Service Pack 2 | Instalar [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Requisitos de Microsoft .NET Framework

En la tabla siguiente se muestran los requisitos de .NET Framework para Windows PowerShell.

| Version | Requisito de .NET |
| ----- | ----- |
| Windows PowerShell 5.1 | Requiere la instalación completa de Microsoft .NET Framework 4.5. Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada. |
| Windows PowerShell 5.0 | Requiere la instalación completa de Microsoft .NET Framework 4.5. Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada. |
| Windows PowerShell 4.0 | Requiere la instalación completa de Microsoft .NET Framework 4.5. Windows 8.1 y Windows Server 2012 R2 incluyen Microsoft .NET Framework 4.5 de manera predeterminada. |
| Windows PowerShell 3.0 | Requiere la instalación completa de Microsoft .NET Framework 4. Windows 8 y Windows Server 2012 incluyen Microsoft .NET Framework 4.5 de manera predeterminada, con lo que se cumple este requisito. |

Use los vínculos siguientes para descargar Microsoft .NET Framework desde el Centro de descarga de Microsoft.

| Version | Vínculo |
| ----- | ----- |
| .NET Framework 4.5 (`dotNetFx45_Full_setup.exe`) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) |
| .NET Framework 4 (`dotNetFx40_Full_setup.exe`) | [Microsoft .NET Framework 4 (instalador web)](https://www.microsoft.com/en-us/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0

Windows PowerShell 5.0 requiere que Windows Management Framework 4.0 esté preinstalado en Windows Server 2008 R2 SP1 y Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0

Windows PowerShell 3.0 y Windows PowerShell 4.0 requieren WS-Management 3.0, que admite el servicio WinRM y el protocolo WSMan. Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Instrumental de administración de Windows 3.0

Windows PowerShell 3.0 y Windows PowerShell 4.0 requiere Instrumental de administración de Windows 3.0 (WMI). Este programa está incluido en Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 y Windows Management Framework 3.0. Si este programa no está instalado en el equipo, las características que requieren WMI, como los comandos CIM, no se ejecutan.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0

Windows PowerShell 3.0, Windows PowerShell 4.0 y Windows PowerShell 5.0 se compilan en Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Requisitos de la interfaz gráfica de usuario

Windows PowerShell es una aplicación basada en consola que no requiere una interfaz gráfica de usuario.
Es idónea para equipos que no tienen pantallas, monitores ni interfaz de usuario, como las opciones de instalación de Server Core de Windows Server 2012 R2 o Windows Server 2012.

Algunos elementos requieren una interfaz gráfica de usuario. Para obtener más información, vea el artículo de ayuda de cada elemento.

- Entorno de scripting integrado (ISE) de Windows PowerShell. Para obtener más información, consulte [Introducción a Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).
- Cmdlets
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Show-ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Show-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- Parámetros
  - Parámetro **ShowWindow** del cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).
  - Parámetro **ShowSecurityDescriptorUI** de los cmdlets [Register-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) y [Set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).

## <a name="windows-powershell-engine-requirements"></a>Requisitos del motor de Windows PowerShell

Windows PowerShell 4.0 está diseñado para ser compatible con versiones anteriores de Windows PowerShell 3.0 y Windows PowerShell 2.0. Los cmdlets, proveedores, complementos, módulos y scripts escritos para Windows PowerShell 2.0 y Windows PowerShell 3.0 se ejecutan sin cambios en Windows PowerShell 4.0.

Pero debido a un cambio en la directiva de activación de tiempo de ejecución en Microsoft .NET Framework 4, los programas de host de Windows PowerShell escritos para Windows PowerShell 2.0 y compilados con Common Language Runtime (CLR) 2.0 no se pueden ejecutar sin modificaciones en Windows PowerShell 3.0, que está compilado con CLR 4.0.

El requisito mínimo del motor de Windows PowerShell 2.0 es Microsoft .NET Framework 2.0.50727. Este requisito se cumple mediante Microsoft .NET Framework 3.5 Service Pack 1. Este requisito no se cumple con Microsoft .NET Framework 4 y versiones posteriores de Microsoft .NET Framework.

Para información sobre cómo agregar o instalar el motor de Windows PowerShell 2.0 y agregar o instalar las versiones necesarias de Microsoft .NET Framework, consulte [Instalación del motor de Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Para obtener información sobre cómo iniciar el motor de Windows PowerShell 2.0, consulte [Iniciar el motor de Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Entorno de preinstalación de Windows

Windows PowerShell 2.0, Windows PowerShell 3.0 y Windows PowerShell 4.0 se ejecutan en el Entorno de preinstalación de Windows (Windows PE). Pero no se admiten los cmdlets siguientes.

- Cmdlets del Servicio de transferencia inteligente en segundo plano (BITS). Para más información, vea [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps).
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

El servicio **WinRM** no está presente en Windows PE.

## <a name="see-also"></a>Vea también

[Introducción a Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)

[Instalación de Windows PowerShell](Installing-Windows-PowerShell.md)

[Inicio de Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
