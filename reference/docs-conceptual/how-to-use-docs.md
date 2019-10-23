---
ms.date: 10/20/2019
keywords: powershell, cmdlet
title: Cómo usar la documentación de PowerShell
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: ac1ccdd826f112a11db09af9c628cae013f947ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2019
ms.locfileid: "72676157"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="25cbe-103">Cómo usar la documentación de PowerShell</span><span class="sxs-lookup"><span data-stu-id="25cbe-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="25cbe-104">Le damos la bienvenida a la documentación en línea de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25cbe-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="25cbe-105">Este sitio contiene referencia de cmdlets para las siguientes versiones de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="25cbe-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="25cbe-106">PowerShell 7 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="25cbe-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="25cbe-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="25cbe-107">PowerShell 6</span></span>
- <span data-ttu-id="25cbe-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="25cbe-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="25cbe-109">Búsqueda de artículos y selección de una versión</span><span class="sxs-lookup"><span data-stu-id="25cbe-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="25cbe-110">Hay dos maneras de buscar contenido en Docs. La manera más sencilla es usar el cuadro de filtro en el selector de versión.</span><span class="sxs-lookup"><span data-stu-id="25cbe-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="25cbe-111">Basta con escribir una palabra que aparezca en el título de un artículo.</span><span class="sxs-lookup"><span data-stu-id="25cbe-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="25cbe-112">En la página se muestra una lista de artículos coincidentes.</span><span class="sxs-lookup"><span data-stu-id="25cbe-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="25cbe-113">También puede seleccionar la opción para buscar en todo el sitio de esa lista.</span><span class="sxs-lookup"><span data-stu-id="25cbe-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="25cbe-114">De forma predeterminada, este sitio muestra la documentación de la última versión publicada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25cbe-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="25cbe-115">Algunos cmdlets funcionan de forma diferente en las distintas versiones de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25cbe-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="25cbe-116">Asegúrese de que está viendo la documentación de la versión de PowerShell que está usando.</span><span class="sxs-lookup"><span data-stu-id="25cbe-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="25cbe-117">Use el selector de versión en la parte superior de la página para seleccionar la versión de PowerShell que quiera.</span><span class="sxs-lookup"><span data-stu-id="25cbe-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Selector de versión](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="25cbe-119">Revise el valor `$PSversionTable.PSVersion` para comprobar la versión de PowerShell que usa.</span><span class="sxs-lookup"><span data-stu-id="25cbe-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="25cbe-120">En el ejemplo siguiente se muestra la salida de Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="25cbe-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
