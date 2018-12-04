---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Sintaxis de búsqueda de la Galería
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742863"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="4b8a8-103">Sintaxis de búsqueda de la Galería</span><span class="sxs-lookup"><span data-stu-id="4b8a8-103">Gallery Search Syntax</span></span>

<span data-ttu-id="4b8a8-104">Puede buscar la Galería de PowerShell mediante el [sitio web de la Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="4b8a8-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="4b8a8-105">Sitio web Galería de PowerShell ofrece un control searchbox de texto donde puede usar palabras, frases y expresiones de palabra clave para restringir los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="4b8a8-106">Buscar por palabras clave</span><span class="sxs-lookup"><span data-stu-id="4b8a8-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="4b8a8-107">Búsqueda intenta encontrar documentos relevantes que contiene todos los 3 palabras clave y devolver documentos coincidentes.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="4b8a8-108">Buscar mediante palabras clave y frases</span><span class="sxs-lookup"><span data-stu-id="4b8a8-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="4b8a8-109">Si se escribe una frase entre comillas (""), la búsqueda pasa a buscar la frase determinada en lugar de palabras clave independientes.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="4b8a8-110">Los documentos coincidentes normalmente contendrán la frase exacta "azure sql", incluidas las variaciones en el uso de mayúsculas y minúsculas (por ejemplo, "Azure SQL"), y normalmente también contendrán la palabra "deployment" (implementación).</span><span class="sxs-lookup"><span data-stu-id="4b8a8-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="4b8a8-111">Filtrar por campos</span><span class="sxs-lookup"><span data-stu-id="4b8a8-111">Filtering on fields</span></span>

<span data-ttu-id="4b8a8-112">Puede buscar un ID de paquete específico, o "Id" o "id", u otros campos anteponiendo a los términos de la búsqueda el nombre del campo.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="4b8a8-113">Actualmente, los campos que se pueden buscar son "Id", "Version", "Tags", "Author", "Owner", "Functions", "Cmdlets", "DscResources" y "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="4b8a8-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="4b8a8-114">[¿Cuál es la diferencia entre el ID y el título?</span><span class="sxs-lookup"><span data-stu-id="4b8a8-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="4b8a8-115">El ID es el nombre que se usa en la consola.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-115">ID is the name you use in the console.</span></span> <span data-ttu-id="4b8a8-116">El título es lo que se muestra en la parte superior de la página del paquete en los resultados de la búsqueda].</span><span class="sxs-lookup"><span data-stu-id="4b8a8-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="4b8a8-117">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4b8a8-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="4b8a8-118">busca paquetes con un identificador que contiene "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="4b8a8-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="4b8a8-119">Es otra manera de buscar paquetes con "AzureRM.Profile" en el campo ID.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="4b8a8-120">El filtro "Id" es una coincidencia de subcadena, por lo que si busca lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b8a8-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="4b8a8-121">Esto proporciona resultados que incluyan AzureRM.Profile "y"Azure.Storage".</span><span class="sxs-lookup"><span data-stu-id="4b8a8-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="4b8a8-122">También puede buscar varias palabras clave en un único campo,</span><span class="sxs-lookup"><span data-stu-id="4b8a8-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="4b8a8-123">Además, puede realizar búsquedas de frases con comillas dobles:</span><span class="sxs-lookup"><span data-stu-id="4b8a8-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="4b8a8-124">Para buscar todos los paquetes con la etiqueta DSC.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="4b8a8-125">Para buscar todos los paquetes con la función especificada.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="4b8a8-126">Para buscar todos los paquetes con el cmdlet especificado.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="4b8a8-127">Para buscar todos los paquetes con el nombre del recurso de DSC especificado.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="4b8a8-128">Para buscar todos los paquetes con el valor de PowerShellVersion especificado.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="4b8a8-129">Por último, si usa un campo que no se admite (como "commands"), se omitirá y se buscará en todos los campos.</span><span class="sxs-lookup"><span data-stu-id="4b8a8-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="4b8a8-130">Así pues, la consulta siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b8a8-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="4b8a8-131">se interpreta exactamente igual que esta consulta:</span><span class="sxs-lookup"><span data-stu-id="4b8a8-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
