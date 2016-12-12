---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_pseditions
ms.technology: powershell
ms.openlocfilehash: fddac6b6741150a0d809dc434a7a14b646434e01
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="items-with-compatible-powershell-editions"></a>Elementos con las ediciones compatibles de PowerShell
A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>La Galería de PowerShell extrae metadatos de PSEditions compatibles y permite filtrar los elementos compatibles con ediciones específicas de PowerShell

Si en un elemento se han especificado PSEditions compatibles, se enumerarán como parte de "Ediciones de PowerShell" en la página de visualización del elemento y en los resultados de los elementos.
![Página de visualización del elemento con PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Buscar elementos en la interfaz de usuario de la Galería que funciona en PowerShellCore
Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los elementos de la Galería de PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.
![Resultados de la búsqueda de elementos compatibles con Core PSEdition](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.
![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Obtener más detalles sobre la creación y la búsqueda de elementos con ediciones compatibles de PowerShell
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[Módulos con PSEditions](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[Scripts con PSEditions](../psget/script/scriptwithpseditionsupport.md)

