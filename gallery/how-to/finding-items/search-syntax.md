---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Sintaxis de búsqueda de la Galería
ms.openlocfilehash: 4c0e357957ef970826ee90868db78ac07a14c804
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="e14c8-103">Sintaxis de búsqueda de la Galería</span><span class="sxs-lookup"><span data-stu-id="e14c8-103">Gallery Search Syntax</span></span>

<span data-ttu-id="e14c8-104">La Galería de PowerShell ofrece un cuadro de búsqueda de texto en el que puede usar palabras, frases y expresiones de palabra clave para restringir los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="e14c8-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="e14c8-105">Buscar por palabras clave</span><span class="sxs-lookup"><span data-stu-id="e14c8-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="e14c8-106">La búsqueda hará todo lo posible por encontrar documentos relevantes que contengan las tres palabras clave y devolver documentos coincidentes.</span><span class="sxs-lookup"><span data-stu-id="e14c8-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="e14c8-107">Buscar mediante palabras clave y frases</span><span class="sxs-lookup"><span data-stu-id="e14c8-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="e14c8-108">Si se escribe una frase entre comillas (""), la búsqueda pasa a buscar la frase determinada en lugar de palabras clave independientes.</span><span class="sxs-lookup"><span data-stu-id="e14c8-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="e14c8-109">Los documentos coincidentes normalmente contendrán la frase exacta "azure sql", incluidas las variaciones en el uso de mayúsculas y minúsculas (por ejemplo, "Azure SQL"), y normalmente también contendrán la palabra "deployment" (implementación).</span><span class="sxs-lookup"><span data-stu-id="e14c8-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="e14c8-110">Filtrar por campos</span><span class="sxs-lookup"><span data-stu-id="e14c8-110">Filtering on fields</span></span>

<span data-ttu-id="e14c8-111">Puede buscar un ID de elemento específico (o "Id" o "id") u otros campos anteponiendo a los términos de la búsqueda el nombre del campo.</span><span class="sxs-lookup"><span data-stu-id="e14c8-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="e14c8-112">Actualmente, los campos que se pueden buscar son "Id", "Version", "Tags", "Author", "Owner", "Functions", "Cmdlets", "DscResources" y "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="e14c8-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="e14c8-113">[¿Cuál es la diferencia entre el ID y el título?</span><span class="sxs-lookup"><span data-stu-id="e14c8-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="e14c8-114">El ID es el nombre que se usa en la consola.</span><span class="sxs-lookup"><span data-stu-id="e14c8-114">ID is the name you use in the console.</span></span> <span data-ttu-id="e14c8-115">El título es lo que se muestra en la parte superior de la página del elemento en los resultados de la búsqueda].</span><span class="sxs-lookup"><span data-stu-id="e14c8-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="e14c8-116">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e14c8-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="e14c8-117">busca elementos con "PSReadline" o "AzureRM.Profile" en el campo ID, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e14c8-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="e14c8-118">es otra manera de buscar elementos con "AzureRM.Profile" en el campo ID.</span><span class="sxs-lookup"><span data-stu-id="e14c8-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="e14c8-119">El filtro "Id" es una coincidencia de subcadena, por lo que si busca lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e14c8-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="e14c8-120">obtendrá resultados como "AzureRM.Profile" y "Azure.Storage".</span><span class="sxs-lookup"><span data-stu-id="e14c8-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="e14c8-121">También puede buscar varias palabras clave en un único campo,</span><span class="sxs-lookup"><span data-stu-id="e14c8-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="e14c8-122">o mezclar y combinar campos.</span><span class="sxs-lookup"><span data-stu-id="e14c8-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="e14c8-123">También puede buscar frases:</span><span class="sxs-lookup"><span data-stu-id="e14c8-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="e14c8-124">Para buscar todos los elementos con la etiqueta DSC.</span><span class="sxs-lookup"><span data-stu-id="e14c8-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="e14c8-125">Para buscar todos los elementos con la función especificada.</span><span class="sxs-lookup"><span data-stu-id="e14c8-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="e14c8-126">Para buscar todos los elementos con el cmdlet especificado.</span><span class="sxs-lookup"><span data-stu-id="e14c8-126">To search all items with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="e14c8-127">Para buscar todos los elementos con el nombre del recurso de DSC especificado.</span><span class="sxs-lookup"><span data-stu-id="e14c8-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="e14c8-128">Para buscar todos los elementos con el valor de PowerShellVersion especificado.</span><span class="sxs-lookup"><span data-stu-id="e14c8-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="e14c8-129">Por último, si usa un campo que no se admite (como "commands"), se omitirá y se buscará en todos los campos.</span><span class="sxs-lookup"><span data-stu-id="e14c8-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="e14c8-130">Así pues, la consulta siguiente:</span><span class="sxs-lookup"><span data-stu-id="e14c8-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="e14c8-131">se interpreta exactamente igual que esta consulta:</span><span class="sxs-lookup"><span data-stu-id="e14c8-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage