---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Paquetes con sistemas operativos o ediciones compatibles de PowerShell
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328446"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Paquetes con sistemas operativos o ediciones compatibles de PowerShell

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

## <a name="searching-by-powershell-edition"></a>Búsqueda por edición de PowerShell

Las dos ediciones de PowerShell son:
- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>La Galería de PowerShell permite filtrar paquetes compatibles para determinadas ediciones de PowerShell

Si en un paquete se han especificado PSEditions compatibles, se enumeran como parte de "Ediciones de PowerShell" en la página de visualización del paquete y en los resultados de los paquetes.
También puede buscar paquetes compatibles con PowerShell.

![Página de visualización del elemento con PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Buscar paquetes en la interfaz de usuario de la Galería que funcionan en PowerShell Core

Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los paquetes de la Galería de PowerShell.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.

![Resultados de la búsqueda de elementos compatibles con Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.

![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Buscar paquetes para encontrar las ediciones compatibles con PowerShell
Puede especificar etiquetas para filtrar por las ediciones de PowerShell y el sistema operativo.
Se usa el cmdlet `Find-Package` especificando el parámetro `-Tag` para especificar la edición (y el sistema operativo) objetivo.
Por ejemplo:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Buscar por sistema operativo

Dado que PowerShell Core está disponible para Windows, Linux y MacOS, los paquetes en la Galería pueden estar diseñados para cualquier combinación de estos sistemas operativos. En la interfaz de usuario de la galería, use las siguientes etiquetas de búsqueda para buscar paquetes etiquetados por sistema operativo:

- Etiquetas: "Windows"
- Etiquetas: "Linux"
- Etiquetas: "MacOS"

Puede especificar estas etiquetas en `Find-Module` (y otros cmdlets del módulo PowerShellGet), por ejemplo:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Buscar por varias compatibilidades

Puede buscar un paquete que tenga varias compatibilidades con la sintaxis siguiente:

Etiquetas: "Compatibilidad1" "Compatibilidad2"

Por ejemplo, si busca un paquete con compatibilidad de PowerShell Core que se ejecuta en ambas máquinas Windows y Linux, use las etiquetas de búsqueda:

Etiquetas: "PSEdition_Core" "Windows" "Linux"

Para buscar con PowerShell, puede usar `Find-Module` (y los otros cmdlets del módulo PowerShellGet), por ejemplo:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Obtener más detalles sobre la creación y la búsqueda de paquetes con ediciones compatibles de PowerShell

- [Módulos con PSEditions](../../concepts/module-psedition-support.md)
- [Scripts con PSEditions](../../concepts/script-psedition-support.md)
