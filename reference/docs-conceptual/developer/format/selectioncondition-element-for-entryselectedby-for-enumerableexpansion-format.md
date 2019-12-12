---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362014"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="117d4-102">Elemento SelectionCondition para EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="117d4-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="117d4-103">Define la condición que debe existir para expandir los objetos de colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="117d4-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="117d4-104">Elemento de configuración (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy para EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="117d4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="117d4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="117d4-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="117d4-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="117d4-106">Attributes and Elements</span></span>

<span data-ttu-id="117d4-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="117d4-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="117d4-108">Debe especificar un único `PropertyName` o un elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="117d4-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="117d4-109">Los elementos `SelectionSetName` y `TypeName` son opcionales.</span><span class="sxs-lookup"><span data-stu-id="117d4-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="117d4-110">Puede especificar uno de los dos elementos.</span><span class="sxs-lookup"><span data-stu-id="117d4-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="117d4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="117d4-111">Attributes</span></span>

<span data-ttu-id="117d4-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="117d4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="117d4-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="117d4-113">Child Elements</span></span>

|<span data-ttu-id="117d4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="117d4-114">Element</span></span>|<span data-ttu-id="117d4-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="117d4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="117d4-116">Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="117d4-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="117d4-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="117d4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="117d4-118">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="117d4-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="117d4-119">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="117d4-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="117d4-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="117d4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="117d4-121">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="117d4-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="117d4-122">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="117d4-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="117d4-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="117d4-123">Optional element.</span></span><br /><br /> <span data-ttu-id="117d4-124">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="117d4-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="117d4-125">Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="117d4-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="117d4-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="117d4-126">Optional element.</span></span><br /><br /> <span data-ttu-id="117d4-127">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="117d4-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="117d4-128">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="117d4-128">Parent Elements</span></span>

|<span data-ttu-id="117d4-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="117d4-129">Element</span></span>|<span data-ttu-id="117d4-130">Descripción</span><span class="sxs-lookup"><span data-stu-id="117d4-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="117d4-131">Elemento EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="117d4-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="117d4-132">Define qué objetos de colección .NET se expanden mediante esta definición.</span><span class="sxs-lookup"><span data-stu-id="117d4-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="117d4-133">Observaciones</span><span class="sxs-lookup"><span data-stu-id="117d4-133">Remarks</span></span>

<span data-ttu-id="117d4-134">Cada definición debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="117d4-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="117d4-135">Cuando se define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="117d4-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="117d4-136">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="117d4-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="117d4-137">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="117d4-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="117d4-138">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para la reproducción de datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="117d4-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="117d4-139">Para obtener más información sobre otros componentes de una vista amplia, vea [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="117d4-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="117d4-140">Véase también</span><span class="sxs-lookup"><span data-stu-id="117d4-140">See Also</span></span>

[<span data-ttu-id="117d4-141">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="117d4-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="117d4-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="117d4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
