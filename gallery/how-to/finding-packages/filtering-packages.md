---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtración de los resultados de la búsqueda
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084409"
---
# <a name="filtering-search-results"></a><span data-ttu-id="6c34d-103">Filtración de los resultados de la búsqueda</span><span class="sxs-lookup"><span data-stu-id="6c34d-103">Filtering search results</span></span>

<span data-ttu-id="6c34d-104">La pestaña [Paquetes](https://www.powershellgallery.com/packages) muestra todos los paquetes disponibles en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c34d-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="6c34d-105">Hay varias maneras de filtrar, ordenar y buscar los paquetes.</span><span class="sxs-lookup"><span data-stu-id="6c34d-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="6c34d-106">Para más información sobre un paquete determinado, haga clic en el paquete.</span><span class="sxs-lookup"><span data-stu-id="6c34d-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="6c34d-107">Filtrar por</span><span class="sxs-lookup"><span data-stu-id="6c34d-107">Filter By</span></span>

<span data-ttu-id="6c34d-108">La lista desplegable bajo "Filtrar por" permite a los usuarios filtrar los resultados por:</span><span class="sxs-lookup"><span data-stu-id="6c34d-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="6c34d-109">Incluir versión preliminar</span><span class="sxs-lookup"><span data-stu-id="6c34d-109">Include Prerelease</span></span>
- <span data-ttu-id="6c34d-110">Solo estable</span><span class="sxs-lookup"><span data-stu-id="6c34d-110">Stable Only</span></span>

<span data-ttu-id="6c34d-111">Para obtener información acerca de "Versión preliminar" y "Estable", consulte [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versiones preliminares agregadas a PowerShellGet y la Galería de PowerShell) en el blog del equipo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c34d-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="6c34d-112">Las casillas bajo la lista desplegable permiten a los usuarios filtrar los resultados por:</span><span class="sxs-lookup"><span data-stu-id="6c34d-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="6c34d-113">Tipos de paquetes</span><span class="sxs-lookup"><span data-stu-id="6c34d-113">Package Types</span></span>
  - <span data-ttu-id="6c34d-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="6c34d-114">Module</span></span>
  - <span data-ttu-id="6c34d-115">Script</span><span class="sxs-lookup"><span data-stu-id="6c34d-115">Script</span></span>
- <span data-ttu-id="6c34d-116">Categorías</span><span class="sxs-lookup"><span data-stu-id="6c34d-116">Categories</span></span>
  - <span data-ttu-id="6c34d-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6c34d-117">Cmdlet</span></span>
  - <span data-ttu-id="6c34d-118">Recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="6c34d-118">DSC Resource</span></span>
  - <span data-ttu-id="6c34d-119">Función</span><span class="sxs-lookup"><span data-stu-id="6c34d-119">Function</span></span>
  - <span data-ttu-id="6c34d-120">Capacidad de rol</span><span class="sxs-lookup"><span data-stu-id="6c34d-120">Role Capability</span></span>
  - <span data-ttu-id="6c34d-121">Flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="6c34d-121">Workflow</span></span>

<span data-ttu-id="6c34d-122">Para ver solo módulos en la Galería de PowerShell, active Módulo en Tipos de paquetes.</span><span class="sxs-lookup"><span data-stu-id="6c34d-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="6c34d-123">De igual manera, para ver solo scripts en la Galería de PowerShell, active Script en Tipos de paquetes.</span><span class="sxs-lookup"><span data-stu-id="6c34d-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="6c34d-124">Los filtros son inclusivos.</span><span class="sxs-lookup"><span data-stu-id="6c34d-124">Filters are inclusive.</span></span>
> <span data-ttu-id="6c34d-125">Ejemplo: Un paquete que contenga cmdlets y funciones aparecerá si se activa Cmdlet o Función, o ambos.</span><span class="sxs-lookup"><span data-stu-id="6c34d-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="6c34d-126">Si no se selecciona ninguna opción, el paquete no aparecerá.</span><span class="sxs-lookup"><span data-stu-id="6c34d-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="6c34d-127">Del mismo modo, si se seleccionan todas las categorías, solo aparecerán los paquetes que contengan alguna de esas categorías.</span><span class="sxs-lookup"><span data-stu-id="6c34d-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="6c34d-128">**No aparecerán los paquetes que no pertenezcan a ninguna de esas categorías.**</span><span class="sxs-lookup"><span data-stu-id="6c34d-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="6c34d-129">Ordenar por</span><span class="sxs-lookup"><span data-stu-id="6c34d-129">Sort By</span></span>

<span data-ttu-id="6c34d-130">La lista desplegable Ordenar por permite a los usuarios ordenar los resultados según los criterios siguientes:</span><span class="sxs-lookup"><span data-stu-id="6c34d-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="6c34d-131">Popularidad: la popularidad está determinada por el número de descargas</span><span class="sxs-lookup"><span data-stu-id="6c34d-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="6c34d-132">A-Z: alfabéticamente según el nombre de paquete</span><span class="sxs-lookup"><span data-stu-id="6c34d-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="6c34d-133">Reciente: los paquetes aparecen ordenados por fecha de publicación</span><span class="sxs-lookup"><span data-stu-id="6c34d-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="6c34d-134">Cuadro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="6c34d-134">Search Box</span></span>

<span data-ttu-id="6c34d-135">El cuadro de búsqueda permite a los usuarios buscar paquetes por palabras clave.</span><span class="sxs-lookup"><span data-stu-id="6c34d-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="6c34d-136">Para obtener más información, consulte [Sintaxis de búsqueda de la Galería](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="6c34d-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
