---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Paquetes con las ediciones de PowerShell o el sistema operativo compatible
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747711"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Paquetes con las ediciones de PowerShell o en sistemas operativos compatibles

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

## <a name="searching-by-powershell-edition"></a>Buscar por edición de PowerShell 
Las dos ediciones de Powershell son:
- Desktop Edition Basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y el escritorio de Windows.
- **Core Edition:** Basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a versiones de PowerShell que se ejecutan en las ediciones de superficie reducida de Windows como Nano Server y Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Galería de PowerShell le permite filtrar paquetes compatibles para determinadas ediciones de PowerShell

Si un paquete tiene compatible PSEditions especificado, que aparecen como parte de 'Ediciones de PowerShell' en la página de presentación de paquete y también en los resultados de los paquetes.
También puede buscar paquetes compatibles con PowerShell.

![Página de visualización del elemento con PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Buscar paquetes en la Galería de la interfaz de usuario que funcionan en PowerShell Core

Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los paquetes de la Galería de PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.

![Resultados de la búsqueda de elementos compatibles con Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.

![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Buscar paquetes para encontrar las ediciones compatibles con PowerShell
Puede especificar etiquetas para filtrar para las ediciones de PowerShell y el sistema operativo. Usa el `Find-Package` cmdlet especificando el `-Tag` parámetro para especificar la edición (y el sistema operativo) tiene como destino.
Así:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Búsqueda por el sistema operativo 

Dado que PowerShell Core está disponible para Windows, Linux y MacOS, los paquetes en la Galería pueden estar diseñados para cualquier combinación de estos sistemas operativos. En la Galería de la interfaz de usuario use las siguientes etiquetas de búsquedas para encontrar los paquetes etiquetados por sistema operativo:

- Etiquetas: "Windows"
- Etiquetas: "Linux"
- Etiquetas: "MacOS" 

Puede especificar estas etiquetas en `Find-Module` (y otros cmdlets del módulo PowerShellGet), similar al siguiente:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Búsqueda de varias compatibilidades

Puede buscar un paquete que tenga varias compatibilidades con la sintaxis: 

Etiquetas "Compatibility1" "2" 

Por ejemplo, si busca un paquete de compatibilidad de núcleo de PowerShell que se ejecuta en máquinas mi Windows y Linux, use las etiquetas de búsqueda:

Etiquetas "PSEdition_Core", "Windows", "Linux" 

Para buscar mediante PowerShell, puede usar el `Find-Module` (y los otros cmdlets del módulo PowerShellGet), similar al siguiente:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Obtener más detalles sobre la creación y la búsqueda de paquetes con ediciones compatibles de PowerShell

- [Módulos con PSEditions](../../concepts/module-psedition-support.md)
- [Scripts con PSEditions](../../concepts/script-psedition-support.md)
