---
title: Elemento EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855591"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="2346e-102">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="2346e-103">Define los tipos de .NET que usan esta definición o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="2346e-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="2346e-104">Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2346e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2346e-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2346e-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2346e-106">Attributes and Elements</span></span>

<span data-ttu-id="2346e-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="2346e-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2346e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="2346e-108">Attributes</span></span>

<span data-ttu-id="2346e-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2346e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2346e-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2346e-110">Child Elements</span></span>

|<span data-ttu-id="2346e-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="2346e-111">Element</span></span>|<span data-ttu-id="2346e-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="2346e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2346e-113">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2346e-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2346e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="2346e-115">Define la condición que debe existir para expandir los objetos de la colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="2346e-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="2346e-116">Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2346e-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2346e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2346e-118">Especifica un conjunto de tipos de .NET que usan esta definición de cómo se expanden los objetos de colección.</span><span class="sxs-lookup"><span data-stu-id="2346e-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="2346e-119">Elemento TypeName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2346e-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2346e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2346e-121">Especifica un tipo .NET que usa esta definición de cómo se expanden los objetos de colección.</span><span class="sxs-lookup"><span data-stu-id="2346e-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2346e-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2346e-122">Parent Elements</span></span>

|<span data-ttu-id="2346e-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="2346e-123">Element</span></span>|<span data-ttu-id="2346e-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="2346e-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2346e-125">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="2346e-126">Define cómo determinados de .NET de colección, los objetos se expanden cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="2346e-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2346e-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2346e-127">Remarks</span></span>

<span data-ttu-id="2346e-128">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para una entrada de definición.</span><span class="sxs-lookup"><span data-stu-id="2346e-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="2346e-129">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="2346e-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="2346e-130">Condiciones de selección se usan para definir una condición que debe existir para que la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o que se evalúa como un valor de propiedad concreto o un script para `true`.</span><span class="sxs-lookup"><span data-stu-id="2346e-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="2346e-131">Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2346e-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2346e-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="2346e-132">See Also</span></span>

[<span data-ttu-id="2346e-133">Definir condiciones para mostrar datos</span><span class="sxs-lookup"><span data-stu-id="2346e-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2346e-134">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="2346e-135">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2346e-136">Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2346e-137">Elemento TypeName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2346e-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2346e-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2346e-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
