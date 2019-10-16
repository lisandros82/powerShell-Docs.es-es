---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361994"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="ac8c2-102">Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ac8c2-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="ac8c2-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="ac8c2-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="ac8c2-105">Elemento de configuración elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansions (Format) elemento EntrySelectedBy para EnumerableExpansion (Format) elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format) elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ac8c2-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac8c2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ac8c2-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac8c2-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ac8c2-107">Attributes and Elements</span></span>

<span data-ttu-id="ac8c2-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac8c2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac8c2-109">Attributes</span></span>

<span data-ttu-id="ac8c2-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac8c2-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ac8c2-111">Child Elements</span></span>

<span data-ttu-id="ac8c2-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac8c2-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ac8c2-113">Parent Elements</span></span>

|<span data-ttu-id="ac8c2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac8c2-114">Element</span></span>|<span data-ttu-id="ac8c2-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="ac8c2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac8c2-116">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ac8c2-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ac8c2-117">Define la condición que debe existir para expandir los objetos de colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac8c2-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ac8c2-118">Text Value</span></span>

<span data-ttu-id="ac8c2-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac8c2-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ac8c2-120">Remarks</span></span>

<span data-ttu-id="ac8c2-121">La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="ac8c2-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ac8c2-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ac8c2-123">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="ac8c2-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="ac8c2-124">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ac8c2-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8c2-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="ac8c2-125">See Also</span></span>

[<span data-ttu-id="ac8c2-126">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="ac8c2-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ac8c2-127">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ac8c2-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ac8c2-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac8c2-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
