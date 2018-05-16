---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Elementos con las ediciones compatibles de PowerShell
ms.openlocfilehash: dd2c67417994e960845f7cef09320a0f688a0212
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="27a5f-103">Elementos con las ediciones compatibles de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27a5f-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="27a5f-104">A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.</span><span class="sxs-lookup"><span data-stu-id="27a5f-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="27a5f-105">**Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="27a5f-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="27a5f-106">**Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="27a5f-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="27a5f-107">La Galería de PowerShell extrae metadatos de PSEditions compatibles y permite filtrar los elementos compatibles con ediciones específicas de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27a5f-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="27a5f-108">Si en un elemento se han especificado PSEditions compatibles, se enumerarán como parte de "Ediciones de PowerShell" en la página de visualización del elemento y en los resultados de los elementos.</span><span class="sxs-lookup"><span data-stu-id="27a5f-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![Página de visualización del elemento con PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="27a5f-110">Buscar elementos en la interfaz de usuario de la Galería que funciona en PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="27a5f-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="27a5f-111">Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los elementos de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27a5f-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="27a5f-112">Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="27a5f-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Resultados de la búsqueda de elementos compatibles con Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="27a5f-114">Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="27a5f-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="27a5f-116">Obtener más detalles sobre la creación y la búsqueda de elementos con ediciones compatibles de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27a5f-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="27a5f-117">Módulos con PSEditions</span><span class="sxs-lookup"><span data-stu-id="27a5f-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="27a5f-118">Scripts con PSEditions</span><span class="sxs-lookup"><span data-stu-id="27a5f-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)