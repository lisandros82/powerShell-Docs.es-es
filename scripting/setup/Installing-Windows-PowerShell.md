---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Instalación de Windows PowerShell"
ms.technology: powershell
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: fd0336b66312293c434ae2c5ad5a7899c20777ff
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="installing-windows-powershell"></a>Instalación de Windows PowerShell
Windows® 8 y Windows Server® 2012 incluyen Windows PowerShell 3.0 y todos los requisitos previos. El sistema también incluye el motor de Windows PowerShell 2.0 para mantener la compatibilidad con versiones anteriores de los programas host que no pueden usar Windows PowerShell 3.0.

En este tema se explica cómo instalar Windows PowerShell 3.0 en sistemas anteriores e instalar y habilitar las características necesarias.

Este tema incluye las siguientes secciones:

-   [Instalar Windows PowerShell en Windows 8 y Windows Server 2012](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Instalar Windows PowerShell en Windows 7 y Windows Server 2008 R2](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Instalar Windows PowerShell en Windows Server 2008](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Instalar Windows PowerShell en Server Core](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Implementar Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Instalar el motor de Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="a-namebkmkinstallingonwindows8andwindowsserver2012ainstalling-windows-powershell-on-windows-8-and-windows-server-2012"></a><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Instalar Windows PowerShell en Windows 8 y Windows Server 2012
Windows PowerShell 3.0 se entrega instalado, configurado y listo para usar. Windows PowerShell Integrated Scripting Environment (ISE) está instalado y habilitado. Para más información sobre cómo iniciar Windows PowerShell, vea [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) (Iniciar Windows PowerShell en Windows 8) y [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell) (Iniciar Windows PowerShell en Windows Server 2012).

## <a name="a-namebkmkinstallingonwindows7andwindowsserver2008r2ainstalling-windows-powershell-on-windows-7-and-windows-server-2008-r2"></a><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Instalar Windows PowerShell en Windows 7 y Windows Server 2008 R2
En estas instrucciones se explica cómo instalar Windows PowerShell 3.0 en equipos que ejecutan Windows 7 con Service Pack 1 y Windows Server 2008 R2 con Service Pack 1. Se ofrecen instrucciones de instalación independientes a continuación para equipos que ejecutan la opción de instalación Server Core de Windows Server 2008 R2.

#### <a name="getting-ready-to-install"></a>Preparativos para la instalación

-   Antes de instalar Windows Management Framework 3.0, desinstale todas las versiones anteriores de Windows Management Framework 3.0.

#### <a name="to-install-windows-powershell-30"></a>Para instalar Windows PowerShell 3.0

1.  Realice la instalación completa de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    O bien, instale Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Instale Windows Management Framework 3.0 desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Para más información sobre cómo iniciar Windows PowerShell 3.0, vea [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md) (Iniciar Windows PowerShell en versiones anteriores de Windows).

## <a name="a-namebkmkinstallingonservercoreainstalling-windows-powershell-on-server-core"></a><a name="BKMK_InstallingOnServerCore"></a>Instalar Windows PowerShell en Server Core
En estas instrucciones se explica cómo instalar Windows PowerShell 3.0 en equipos con la opción de instalación Server Core de Windows Server 2008 R2 con Service Pack 1.

Los primeros pasos del procedimiento usan comandos de Administración y mantenimiento de imágenes de implementación (DISM) para instalar Microsoft .NET Framework 2.0 para Server Core y Windows PowerShell 2.0. Estos programas son requisitos previos para Windows Management Framework 3.0, que se instala en un paso posterior.

#### <a name="getting-ready-to-install"></a>Preparativos para la instalación

-   Antes de instalar Windows Management Framework 3.0, desinstale todas las versiones anteriores de Windows Management Framework 3.0.

#### <a name="to-install-windows-powershell-30"></a>Para instalar Windows PowerShell 3.0

1.  Iniciar Cmd.exe

2.  Ejecute los siguientes comandos DISM. Estos comandos instalan .NET Framework 2.0 y Windows PowerShell 2.0.

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Realice la instalación completa de Microsoft .NET Framework 4.0 para Server Core desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Instale Windows Management Framework 3.0 desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="a-namebkmkinstallingonwindowsserver2008lhainstalling-windows-powershell-on-windows-server-2008"></a><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Instalar Windows PowerShell en Windows Server 2008
En estas instrucciones se explica cómo instalar Windows PowerShell 3.0 en equipos que ejecutan Windows Server 2008 con Service Pack 2.

En los sistemas Windows Server 2008, Windows Management Framework (Windows PowerShell 2.0, KB968930) es un requisito previo para Windows Management Framework 3.0. La característica de "protección ampliada para la autenticación" protege el equipo frente a ataques de reenvío de autenticación y le permite usar el parámetro **UseSSL** al crear sesiones remotas. Para instalar Windows PowerShell 3.0 y el motor de Windows PowerShell 2.0, utilice el procedimiento siguiente.

#### <a name="getting-ready-to-install"></a>Preparativos para la instalación

-   Antes de instalar Windows Management Framework 3.0, desinstale todas las versiones anteriores de Windows Management Framework 3.0.

#### <a name="to-install-windows-powershell-30"></a>Para instalar Windows PowerShell 3.0

1.  Instale Microsoft .NET Framework 3.5 con Service Pack 1 desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Instale Windows Management Framework (Windows PowerShell 2.0, KB 968930) desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Realice la instalación completa de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    O bien, instale Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Instale la característica de "protección ampliada para la autenticación" (KB 968389) desde [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Instale Windows Management Framework 3.0 desde el Centro de descarga de Microsoft en [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="see-also"></a>Véase también
- [Requisitos del sistema de Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Inicio de Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

