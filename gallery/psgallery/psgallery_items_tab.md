---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a><span data-ttu-id="a55a2-103">Pestaña Elementos</span><span class="sxs-lookup"><span data-stu-id="a55a2-103">Items Tab</span></span>

<span data-ttu-id="a55a2-104">La pestaña [Elementos](https://www.powershellgallery.com/items) muestra todos los elementos disponibles en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a55a2-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="a55a2-105">Hay varias maneras de filtrar, ordenar y buscar los elementos.</span><span class="sxs-lookup"><span data-stu-id="a55a2-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="a55a2-106">Para obtener más información sobre un elemento determinado, haga clic en el elemento.</span><span class="sxs-lookup"><span data-stu-id="a55a2-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="a55a2-107">Filtrar por</span><span class="sxs-lookup"><span data-stu-id="a55a2-107">Filter By</span></span>

<span data-ttu-id="a55a2-108">La lista desplegable bajo "Filtrar por" permite a los usuarios filtrar los resultados por:</span><span class="sxs-lookup"><span data-stu-id="a55a2-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="a55a2-109">Incluir versión preliminar</span><span class="sxs-lookup"><span data-stu-id="a55a2-109">Include Prerelease</span></span>
* <span data-ttu-id="a55a2-110">Solo estable</span><span class="sxs-lookup"><span data-stu-id="a55a2-110">Stable Only</span></span>

<span data-ttu-id="a55a2-111">Para obtener información acerca de "Versión preliminar" y "Estable", consulte [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versiones preliminares agregadas a PowerShellGet y la Galería de PowerShell) en el blog del equipo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a55a2-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="a55a2-112">Las casillas bajo la lista desplegable permiten a los usuarios filtrar los resultados por:</span><span class="sxs-lookup"><span data-stu-id="a55a2-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="a55a2-113">Tipos de elemento</span><span class="sxs-lookup"><span data-stu-id="a55a2-113">Item Types</span></span>
  - <span data-ttu-id="a55a2-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="a55a2-114">Module</span></span>
  - <span data-ttu-id="a55a2-115">Script</span><span class="sxs-lookup"><span data-stu-id="a55a2-115">Script</span></span>
* <span data-ttu-id="a55a2-116">Categorías</span><span class="sxs-lookup"><span data-stu-id="a55a2-116">Categories</span></span>
  - <span data-ttu-id="a55a2-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a55a2-117">Cmdlet</span></span>
  - <span data-ttu-id="a55a2-118">Recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="a55a2-118">DSC Resource</span></span>
  - <span data-ttu-id="a55a2-119">Función</span><span class="sxs-lookup"><span data-stu-id="a55a2-119">Function</span></span>
  - <span data-ttu-id="a55a2-120">Capacidad de rol</span><span class="sxs-lookup"><span data-stu-id="a55a2-120">Role Capability</span></span>
  - <span data-ttu-id="a55a2-121">Flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="a55a2-121">Workflow</span></span>

<span data-ttu-id="a55a2-122">Para ver solo módulos en la Galería de PowerShell, active Módulo en Tipos de elementos.</span><span class="sxs-lookup"><span data-stu-id="a55a2-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="a55a2-123">De igual manera, para ver solo scripts en la Galería de PowerShell, active Script en Tipos de elementos.</span><span class="sxs-lookup"><span data-stu-id="a55a2-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="a55a2-124">Los filtros son inclusivos.</span><span class="sxs-lookup"><span data-stu-id="a55a2-124">Filters are inclusive.</span></span>
> <span data-ttu-id="a55a2-125">Por ejemplo, un elemento que contenga cmdlets y funciones aparecerá si se activa Cmdlet o Función (o ambos).</span><span class="sxs-lookup"><span data-stu-id="a55a2-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="a55a2-126">Si no se selecciona ninguna opción, el elemento no aparecerá.</span><span class="sxs-lookup"><span data-stu-id="a55a2-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="a55a2-127">Del mismo modo, si se seleccionan todas las categorías, solo aparecerán los elementos que contengan alguna de esas categorías.</span><span class="sxs-lookup"><span data-stu-id="a55a2-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="a55a2-128">**No aparecerán los elementos que no pertenezcan a ninguna de esas categorías.**</span><span class="sxs-lookup"><span data-stu-id="a55a2-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="a55a2-129">Ordenar por</span><span class="sxs-lookup"><span data-stu-id="a55a2-129">Sort By</span></span>

<span data-ttu-id="a55a2-130">La lista desplegable Ordenar por permite a los usuarios ordenar los resultados según los criterios siguientes:</span><span class="sxs-lookup"><span data-stu-id="a55a2-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="a55a2-131">Popularidad: la popularidad está determinada por el número de descargas</span><span class="sxs-lookup"><span data-stu-id="a55a2-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="a55a2-132">A-Z: alfabéticamente según el nombre de elemento</span><span class="sxs-lookup"><span data-stu-id="a55a2-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="a55a2-133">Reciente: los elementos aparecen ordenados por fecha de publicación</span><span class="sxs-lookup"><span data-stu-id="a55a2-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="a55a2-134">Cuadro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="a55a2-134">Search Box</span></span>

<span data-ttu-id="a55a2-135">El cuadro de búsqueda permite a los usuarios buscar elementos por palabras clave.</span><span class="sxs-lookup"><span data-stu-id="a55a2-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="a55a2-136">Para obtener más información, consulte [Sintaxis de búsqueda de la Galería](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="a55a2-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>