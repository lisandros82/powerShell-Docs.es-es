---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064142"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="2e4f4-102">Elemento SelectionCondition para EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="2e4f4-103">Define la condición que debe existir para expandir los objetos de la colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="2e4f4-104">Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración (elemento) SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e4f4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2e4f4-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e4f4-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2e4f4-106">Attributes and Elements</span></span>

<span data-ttu-id="2e4f4-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="2e4f4-108">Debe especificar una sola `PropertyName` o `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="2e4f4-109">El `SelectionSetName` y `TypeName` elementos son opcionales.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="2e4f4-110">Puede especificar uno de cualquier elemento.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e4f4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2e4f4-111">Attributes</span></span>

<span data-ttu-id="2e4f4-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e4f4-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2e4f4-113">Child Elements</span></span>

|<span data-ttu-id="2e4f4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e4f4-114">Element</span></span>|<span data-ttu-id="2e4f4-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e4f4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e4f4-116">Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2e4f4-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2e4f4-118">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2e4f4-119">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2e4f4-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2e4f4-121">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2e4f4-122">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2e4f4-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-123">Optional element.</span></span><br /><br /> <span data-ttu-id="2e4f4-124">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="2e4f4-125">Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2e4f4-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-126">Optional element.</span></span><br /><br /> <span data-ttu-id="2e4f4-127">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e4f4-128">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2e4f4-128">Parent Elements</span></span>

|<span data-ttu-id="2e4f4-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e4f4-129">Element</span></span>|<span data-ttu-id="2e4f4-130">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e4f4-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e4f4-131">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="2e4f4-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="2e4f4-132">Define los objetos de colección de .NET se expanden por esta definición.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e4f4-133">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2e4f4-133">Remarks</span></span>

<span data-ttu-id="2e4f4-134">Cada definición debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2e4f4-135">Al definir una condición de selección, se aplican los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="2e4f4-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2e4f4-136">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2e4f4-137">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2e4f4-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2e4f4-138">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para los datos de la visualización](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2e4f4-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2e4f4-139">Para obtener más información sobre otros componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2e4f4-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e4f4-140">Véase también</span><span class="sxs-lookup"><span data-stu-id="2e4f4-140">See Also</span></span>

[<span data-ttu-id="2e4f4-141">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="2e4f4-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2e4f4-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e4f4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
