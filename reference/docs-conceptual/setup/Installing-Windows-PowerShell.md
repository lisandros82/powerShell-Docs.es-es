---
ms.date: 08/09/2017
keywords: powershell,cmdlet,descargar,instalar,configurar,windows 10,windows 8.1,windows 8.0,windows 7
title: Instalación de Windows PowerShell
ms.openlocfilehash: 89f0f689ebfcd34dd4c8ec3824ec8ab4bddc34d9
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483005"
---
# <a name="installing-windows-powershell"></a>Instalación de Windows PowerShell
A partir de las ediciones Windows 7 SP1 y Windows Server 2008 R2 SP1, Windows PowerShell viene instalado en Windows de forma predeterminada.

Si está interesado en PowerShell 6 y versiones posteriores, debe instalar PowerShell Core en lugar de Windows PowerShell. Para ello, consulte [Instalación de PowerShell Core en Windows](Installing-PowerShell-Core-on-Windows.md).

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

Escriba `powershell` y pulse **ENTRAR** para iniciar PowerShell en la sesión del símbolo del sistema.
Escriba `exit` para finalizar la sesión de PowerShell y volver al símbolo del sistema.

### <a name="windows-server-desktop-editions"></a>Ediciones de escritorio de Windows Server

En todas las ediciones de escritorio, deberá hacer clic en el icono de Windows de la esquina inferior izquierda y empezar a escribir PowerShell.
Se mostrarán las opciones de la consola y el ISE.

La única excepción a la regla anterior se produce en el caso del ISE en Windows Server 2008 R2 SP1. En ese caso, haga clic en el icono de Windows de la esquina inferior izquierda y escriba PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Comprobación de la versión de PowerShell

Para consultar qué versión de PowerShell ha instalado, inicie una consola de PowerShell (o el ISE), escriba `$PSVersionTable` y pulse **ENTRAR**. Busque el valor `PSVersion`.

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

Si está buscando **Azure PowerShell**, puede empezar por el artículo [Overview of Azure PowerShell](https://docs.microsoft.com/powershell/azure) (Información general sobre Azure PowerShell).

De lo contrario, consulte [Install and configure Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps) (Instalación y configuración de Azure PowerShell).

## <a name="see-also"></a>Véase también

- [Requisitos del sistema de Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Inicio de Windows PowerShell](Starting-Windows-PowerShell.md)