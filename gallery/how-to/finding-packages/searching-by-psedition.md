---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Paquetes con ediciones compatibles de PowerShell
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003898"
---
# <a name="packages-with-compatible-powershell-editions"></a>Paquetes con ediciones compatibles de PowerShell

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>La Galería de PowerShell extrae metadatos de PSEditions compatibles y permite filtrar los paquetes compatibles con ediciones específicas de PowerShell.

Si en un paquete se han especificado PSEditions compatibles, se enumerarán como parte de "Ediciones de PowerShell" en la página de visualización del paquete y en los resultados de los paquetes.

![Página de visualización del elemento con PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Buscar paquetes en la interfaz de usuario de la Galería que funciona en PowerShellCore

Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los paquetes de la Galería de PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.

![Resultados de la búsqueda de elementos compatibles con Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.

![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Obtener más detalles sobre la creación y la búsqueda de paquetes con ediciones compatibles de PowerShell

- [Módulos con PSEditions](../../concepts/module-psedition-support.md)
- [Scripts con PSEditions](../../concepts/script-psedition-support.md)
