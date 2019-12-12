---
title: Elemento EntrySelectedBy para EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368804"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="d14ed-102">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="d14ed-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="d14ed-103">Define los tipos .NET que usan esta definición o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="d14ed-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="d14ed-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d14ed-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d14ed-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d14ed-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d14ed-106">Attributes and Elements</span></span>

<span data-ttu-id="d14ed-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="d14ed-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d14ed-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d14ed-108">Attributes</span></span>

<span data-ttu-id="d14ed-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d14ed-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d14ed-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d14ed-110">Child Elements</span></span>

|<span data-ttu-id="d14ed-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d14ed-111">Element</span></span>|<span data-ttu-id="d14ed-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="d14ed-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d14ed-113">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="d14ed-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d14ed-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d14ed-115">Define la condición que debe existir para expandir los objetos de colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="d14ed-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="d14ed-116">Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="d14ed-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d14ed-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d14ed-118">Especifica un conjunto de tipos de .NET que usan esta definición de cómo se expanden los objetos de colección.</span><span class="sxs-lookup"><span data-stu-id="d14ed-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="d14ed-119">Elemento TypeName para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="d14ed-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d14ed-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d14ed-121">Especifica un tipo .NET que usa esta definición de cómo se expanden los objetos de colección.</span><span class="sxs-lookup"><span data-stu-id="d14ed-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d14ed-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d14ed-122">Parent Elements</span></span>

|<span data-ttu-id="d14ed-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="d14ed-123">Element</span></span>|<span data-ttu-id="d14ed-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="d14ed-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d14ed-125">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="d14ed-126">Define cómo se expanden los objetos de colección .NET específicos cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="d14ed-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d14ed-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d14ed-127">Remarks</span></span>

<span data-ttu-id="d14ed-128">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una entrada de definición.</span><span class="sxs-lookup"><span data-stu-id="d14ed-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="d14ed-129">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="d14ed-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="d14ed-130">Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o que un script o un valor de propiedad específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="d14ed-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="d14ed-131">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d14ed-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d14ed-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="d14ed-132">See Also</span></span>

[<span data-ttu-id="d14ed-133">Definir condiciones para Mostrar datos</span><span class="sxs-lookup"><span data-stu-id="d14ed-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d14ed-134">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="d14ed-135">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="d14ed-136">Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="d14ed-137">Elemento TypeName para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d14ed-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="d14ed-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14ed-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
