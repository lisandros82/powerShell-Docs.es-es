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
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="606ac-103">Paquetes con las ediciones de PowerShell o en sistemas operativos compatibles</span><span class="sxs-lookup"><span data-stu-id="606ac-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="606ac-104">A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.</span><span class="sxs-lookup"><span data-stu-id="606ac-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="606ac-105">Buscar por edición de PowerShell</span><span class="sxs-lookup"><span data-stu-id="606ac-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="606ac-106">Las dos ediciones de Powershell son:</span><span class="sxs-lookup"><span data-stu-id="606ac-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="606ac-107">Desktop Edition Basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y el escritorio de Windows.</span><span class="sxs-lookup"><span data-stu-id="606ac-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="606ac-108">**Core Edition:** Basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a versiones de PowerShell que se ejecutan en las ediciones de superficie reducida de Windows como Nano Server y Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="606ac-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="606ac-109">Galería de PowerShell le permite filtrar paquetes compatibles para determinadas ediciones de PowerShell</span><span class="sxs-lookup"><span data-stu-id="606ac-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="606ac-110">Si un paquete tiene compatible PSEditions especificado, que aparecen como parte de 'Ediciones de PowerShell' en la página de presentación de paquete y también en los resultados de los paquetes.</span><span class="sxs-lookup"><span data-stu-id="606ac-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="606ac-111">También puede buscar paquetes compatibles con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="606ac-111">You can also search for compatible packages using PowerShell.</span></span>

![Página de visualización del elemento con PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="606ac-113">Buscar paquetes en la Galería de la interfaz de usuario que funcionan en PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="606ac-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="606ac-114">Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los paquetes de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="606ac-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="606ac-115">Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="606ac-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Resultados de la búsqueda de elementos compatibles con Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="606ac-117">Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="606ac-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="606ac-119">Buscar paquetes para encontrar las ediciones compatibles con PowerShell</span><span class="sxs-lookup"><span data-stu-id="606ac-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="606ac-120">Puede especificar etiquetas para filtrar para las ediciones de PowerShell y el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="606ac-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="606ac-121">Usa el `Find-Package` cmdlet especificando el `-Tag` parámetro para especificar la edición (y el sistema operativo) tiene como destino.</span><span class="sxs-lookup"><span data-stu-id="606ac-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="606ac-122">Así:</span><span class="sxs-lookup"><span data-stu-id="606ac-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="606ac-123">Búsqueda por el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="606ac-123">Searching by Operating System</span></span> 

<span data-ttu-id="606ac-124">Dado que PowerShell Core está disponible para Windows, Linux y MacOS, los paquetes en la Galería pueden estar diseñados para cualquier combinación de estos sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="606ac-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="606ac-125">En la Galería de la interfaz de usuario use las siguientes etiquetas de búsquedas para encontrar los paquetes etiquetados por sistema operativo:</span><span class="sxs-lookup"><span data-stu-id="606ac-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="606ac-126">Etiquetas: "Windows"</span><span class="sxs-lookup"><span data-stu-id="606ac-126">Tags: "Windows"</span></span>
- <span data-ttu-id="606ac-127">Etiquetas: "Linux"</span><span class="sxs-lookup"><span data-stu-id="606ac-127">Tags: "Linux"</span></span>
- <span data-ttu-id="606ac-128">Etiquetas: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="606ac-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="606ac-129">Puede especificar estas etiquetas en `Find-Module` (y otros cmdlets del módulo PowerShellGet), similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="606ac-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="606ac-130">Búsqueda de varias compatibilidades</span><span class="sxs-lookup"><span data-stu-id="606ac-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="606ac-131">Puede buscar un paquete que tenga varias compatibilidades con la sintaxis:</span><span class="sxs-lookup"><span data-stu-id="606ac-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="606ac-132">Etiquetas "Compatibility1" "2"</span><span class="sxs-lookup"><span data-stu-id="606ac-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="606ac-133">Por ejemplo, si busca un paquete de compatibilidad de núcleo de PowerShell que se ejecuta en máquinas mi Windows y Linux, use las etiquetas de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="606ac-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="606ac-134">Etiquetas "PSEdition_Core", "Windows", "Linux"</span><span class="sxs-lookup"><span data-stu-id="606ac-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="606ac-135">Para buscar mediante PowerShell, puede usar el `Find-Module` (y los otros cmdlets del módulo PowerShellGet), similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="606ac-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="606ac-136">Obtener más detalles sobre la creación y la búsqueda de paquetes con ediciones compatibles de PowerShell</span><span class="sxs-lookup"><span data-stu-id="606ac-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="606ac-137">Módulos con PSEditions</span><span class="sxs-lookup"><span data-stu-id="606ac-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="606ac-138">Scripts con PSEditions</span><span class="sxs-lookup"><span data-stu-id="606ac-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
