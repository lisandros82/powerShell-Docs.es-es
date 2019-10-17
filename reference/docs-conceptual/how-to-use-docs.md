---
ms.date: 09/25/2019
keywords: powershell, cmdlet
title: Cómo usar la documentación de PowerShell
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281656"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="64339-103">Cómo usar la documentación de PowerShell</span><span class="sxs-lookup"><span data-stu-id="64339-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="64339-104">Le damos la bienvenida a la documentación en línea de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64339-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="64339-105">Este sitio contiene referencia de cmdlets para las siguientes versiones de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="64339-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="64339-106">PowerShell 7 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="64339-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="64339-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="64339-107">PowerShell 6</span></span>
- <span data-ttu-id="64339-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="64339-108">PowerShell 5.1</span></span>
- <span data-ttu-id="64339-109">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="64339-109">PowerShell 5.0</span></span>
- <span data-ttu-id="64339-110">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="64339-110">PowerShell 4.0</span></span>
- <span data-ttu-id="64339-111">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="64339-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="64339-112">Selección de la versión</span><span class="sxs-lookup"><span data-stu-id="64339-112">Selecting your version</span></span>

<span data-ttu-id="64339-113">De forma predeterminada, este sitio muestra la documentación de la última versión publicada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64339-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="64339-114">Algunos cmdlets funcionan de forma diferente en las distintas versiones de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64339-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="64339-115">Asegúrese de que está viendo la documentación de la versión de PowerShell que está usando.</span><span class="sxs-lookup"><span data-stu-id="64339-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="64339-116">Use el selector de versión en la parte superior de la página para seleccionar la versión de PowerShell que quiera.</span><span class="sxs-lookup"><span data-stu-id="64339-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Selector de versión](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="64339-118">Revise el valor `$PSversionTable.PSVersion` para comprobar la versión de PowerShell que usa.</span><span class="sxs-lookup"><span data-stu-id="64339-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="64339-119">En el ejemplo siguiente se muestra la salida de Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="64339-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="64339-120">Búsqueda de artículos</span><span class="sxs-lookup"><span data-stu-id="64339-120">Searching for articles</span></span>

<span data-ttu-id="64339-121">Hay dos maneras de buscar contenido en Docs. La manera más sencilla es usar el cuadro de filtro en el selector de versión.</span><span class="sxs-lookup"><span data-stu-id="64339-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="64339-122">Basta con escribir una palabra que aparezca en el título de un artículo.</span><span class="sxs-lookup"><span data-stu-id="64339-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="64339-123">En la página se muestra una lista de artículos coincidentes.</span><span class="sxs-lookup"><span data-stu-id="64339-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="64339-124">También puede seleccionar la opción para buscar en todo el sitio de esa lista.</span><span class="sxs-lookup"><span data-stu-id="64339-124">You can also select the option to search the entire site from that list.</span></span>

![cuadro de filtro](images/how-to-use-docs/filter-search.gif)
