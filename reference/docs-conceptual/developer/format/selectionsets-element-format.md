---
title: Elemento SelectionSets (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361874"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="f6f89-102">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="f6f89-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="f6f89-103">Define los conjuntos comunes de objetos .NET que pueden ser utilizados por todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f6f89-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="f6f89-104">Las vistas y los controles del archivo de formato pueden hacer referencia al conjunto completo de objetos usando solo el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="f6f89-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="f6f89-105">Formato del elemento SelectionSets de elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="f6f89-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="f6f89-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f6f89-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6f89-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f6f89-107">Attributes and Elements</span></span>

<span data-ttu-id="f6f89-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSets`.</span><span class="sxs-lookup"><span data-stu-id="f6f89-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="f6f89-109">Cada elemento secundario define un conjunto de objetos a los que se puede hacer referencia mediante el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="f6f89-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="f6f89-110">El orden de los elementos secundarios no es significativo.</span><span class="sxs-lookup"><span data-stu-id="f6f89-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6f89-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f6f89-111">Attributes</span></span>

<span data-ttu-id="f6f89-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f6f89-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6f89-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f6f89-113">Child Elements</span></span>

|<span data-ttu-id="f6f89-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6f89-114">Element</span></span>|<span data-ttu-id="f6f89-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="f6f89-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6f89-116">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="f6f89-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="f6f89-117">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="f6f89-117">Required element.</span></span><br /><br /> <span data-ttu-id="f6f89-118">Define un único conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="f6f89-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6f89-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f6f89-119">Parent Elements</span></span>

|<span data-ttu-id="f6f89-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6f89-120">Element</span></span>|<span data-ttu-id="f6f89-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="f6f89-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6f89-122">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="f6f89-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="f6f89-123">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f6f89-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6f89-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f6f89-124">Remarks</span></span>

<span data-ttu-id="f6f89-125">Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia.</span><span class="sxs-lookup"><span data-stu-id="f6f89-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f6f89-126">Al definir las vistas, puede especificar el conjunto de objetos mediante el nombre del conjunto de selección en lugar de enumerar todos los objetos de cada vista.</span><span class="sxs-lookup"><span data-stu-id="f6f89-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="f6f89-127">Los conjuntos de selección comunes se especifican por su nombre al definir las vistas del archivo de formato o las definiciones de las vistas.</span><span class="sxs-lookup"><span data-stu-id="f6f89-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="f6f89-128">En estos casos, el `SelectionSetName` elemento secundario de los elementos `ViewSelectedBy` y `EntrySelectedBy` especifica el conjunto que se va a utilizar.</span><span class="sxs-lookup"><span data-stu-id="f6f89-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="f6f89-129">Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f6f89-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6f89-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="f6f89-130">See Also</span></span>

[<span data-ttu-id="f6f89-131">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="f6f89-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="f6f89-132">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="f6f89-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f6f89-133">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="f6f89-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f6f89-134">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6f89-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
