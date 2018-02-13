---
ms.date: 2017-08-09
keywords: powershell,cmdlet,descargar,instalar,configurar,windows 10,windows 8.1,windows 8.0,windows 7
title: "Instalación de Windows PowerShell"
ms.openlocfilehash: ec8f09087a5c5f2e7ea6237faa01ea3f447ad1f3
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="installing-windows-powershell"></a>Instalación de Windows PowerShell

A partir de las ediciones Windows 7 SP1 y Windows Server 2008 R2 SP1, PowerShell viene instalado en Windows de forma predeterminada.

Los usuarios de Linux, macOS y Windows que quieran instalar **PowerShell 6** (beta) en su máquina deberán hacer lo siguiente:

1. Obtener PowerShell para el sistema operativo adecuado y su versión específica en [GitHub](https://github.com/powershell/powershell#get-powershell)
1. Instrucciones de instalación
  - [Linux](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [macOS](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md)
  - [Windows](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

PowerShell 6 también está disponible para Docker; consulte las instrucciones de [instalación de Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Búsqueda de PowerShell en Windows 10, 8.1, 8.0 y 7

Encontrar la consola o el ISE (Entorno de scripting integrado por sus siglas en inglés) de PowerShell en Windows puede ser difícil, ya que su ubicación cambia en función de la versión del sistema.

En las tablas siguientes se proporciona información para poder encontrar PowerShell según la versión de Windows que se esté usando.
Todas las versiones que se muestran aquí son las originales, tal y como se publican y sin actualizaciones.

### <a name="for-console"></a>Consola

Version | Ubicación
-- | --
Windows 10 | Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell.
Windows 8.1 u 8.0 | En la pantalla Inicio, empiece a escribir PowerShell.<br/>Si está en el escritorio, haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell.
Windows 7 SP1 | Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell en el cuadro de búsqueda.

### <a name="for-ise"></a>ISE

Version | Ubicación
-- | --
Windows 10 | Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir ISE.
Windows 8.1 u 8.0 | En la pantalla Inicio, escriba **PowerShell ISE**.<br/>Si está en el escritorio, haga clic en el icono de Windows de la esquina inferior izquierda y escriba **PowerShell ISE**.
Windows 7 SP1 | Haga clic en el icono de Windows de la esquina inferior izquierda y empiece a escribir PowerShell en el cuadro de búsqueda.

## <a name="finding-powershell-in-windows-server-versions"></a>Búsqueda de PowerShell en versiones de Windows Server

A partir de Windows Server 2008 R2, el sistema operativo Windows puede instalarse sin la interfaz gráfica de usuario (GUI).
Las ediciones de Windows Server sin GUI se conocen como ediciones **básicas**, mientras que las que sí que tienen GUI se conocen como **de escritorio**.

### <a name="windows-server-core-editions"></a>Ediciones básicas de Windows Server

En todas las ediciones básicas, se mostrará una ventana del símbolo del sistema de Windows al iniciar sesión en el servidor.

Escriba `powershell` y pulse **ENTRAR** para iniciar PowerShell en la sesión del símbolo del sistema. Escriba `exit` para finalizar la sesión de PowerShell y volver al símbolo del sistema.

### <a name="windows-server-desktop-editions"></a>Ediciones de escritorio de Windows Server

En todas las ediciones de escritorio, deberá hacer clic en el icono de Windows de la esquina inferior izquierda y empezar a escribir PowerShell.
Se mostrarán las opciones de la consola y el ISE.

La única excepción a la regla anterior se produce en el caso del ISE en Windows Server 2008 R2 SP1. En ese caso, haga clic en el icono de Windows de la esquina inferior izquierda y escriba PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Comprobación de la versión de PowerShell

Para consultar qué versión de PowerShell ha instalado, inicie una consola de PowerShell (o el ISE), escriba `$PSVersionTable` y pulse **ENTRAR**.

## <a name="upgrading-existing-windows-powershell"></a>Actualización de Windows PowerShell existente

El paquete de instalación de PowerShell está incluido en un instalador WMF.
La versión del instalador WMF coincide con la versión de PowerShell; no hay ningún instalador independiente de Windows PowerShell.

Si debe actualizar la versión existente de PowerShell en Windows, use la tabla siguiente para encontrar el instalador correspondiente a la versión de PowerShell que quiera aplicar.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (consulte Nota 1)<br/>Windows Server 2016 | - | - | - | Instalado
Windows 8.1<br/>Windows Server 2012 R2 | - | Instalado | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | Instalado | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Nota 1**:
  >>
  >> En la versión inicial de Windows 10, con las actualizaciones automáticas habilitadas, PowerShell se actualiza de la versión 5.0 a la 5.1.
  >>
  >> Si no se actualiza la versión original de Windows 10 mediante las actualizaciones de Windows, la versión de PowerShell será la 5.0.

## <a name="need-azure-powershell"></a>Obtención de Azure PowerShell

Si está buscando **Azure PowerShell**, puede empezar por el artículo [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure) (Información general sobre Azure PowerShell).

De lo contrario, consulte [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps) (Instalación y configuración de Azure PowerShell).

## <a name="see-also"></a>Véase también

- [Requisitos del sistema de Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Inicio de Windows PowerShell](Starting-Windows-PowerShell.md)
