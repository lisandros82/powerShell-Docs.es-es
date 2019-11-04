---
title: Elemento SelectionCondition para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364784"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="dfd30-102">Elemento SelectionCondition para EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dfd30-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="dfd30-103">Define la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="dfd30-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="dfd30-104">No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de entrada ancha.</span><span class="sxs-lookup"><span data-stu-id="dfd30-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="dfd30-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dfd30-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dfd30-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfd30-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="dfd30-107">Attributes and Elements</span></span>

<span data-ttu-id="dfd30-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="dfd30-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="dfd30-109">Debe especificar un único elemento `PropertyName` o `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="dfd30-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="dfd30-110">Los elementos `SelectionSetName` y `TypeName` son opcionales.</span><span class="sxs-lookup"><span data-stu-id="dfd30-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="dfd30-111">Puede especificar uno de los dos elementos.</span><span class="sxs-lookup"><span data-stu-id="dfd30-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfd30-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dfd30-112">Attributes</span></span>

<span data-ttu-id="dfd30-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="dfd30-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfd30-114">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="dfd30-114">Child Elements</span></span>

|<span data-ttu-id="dfd30-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfd30-115">Element</span></span>|<span data-ttu-id="dfd30-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="dfd30-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfd30-117">Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="dfd30-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dfd30-118">Optional element.</span></span><br /><br /> <span data-ttu-id="dfd30-119">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="dfd30-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="dfd30-120">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="dfd30-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dfd30-121">Optional element.</span></span><br /><br /> <span data-ttu-id="dfd30-122">Especifica el bloque de script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="dfd30-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="dfd30-123">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="dfd30-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dfd30-124">Optional element.</span></span><br /><br /> <span data-ttu-id="dfd30-125">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="dfd30-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="dfd30-126">Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="dfd30-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dfd30-127">Optional element.</span></span><br /><br /> <span data-ttu-id="dfd30-128">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="dfd30-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dfd30-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="dfd30-129">Parent Elements</span></span>

|<span data-ttu-id="dfd30-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfd30-130">Element</span></span>|<span data-ttu-id="dfd30-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="dfd30-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfd30-132">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="dfd30-133">Define los tipos de .NET que usan esta entrada ancha o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="dfd30-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dfd30-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="dfd30-134">Remarks</span></span>

<span data-ttu-id="dfd30-135">Cada entrada ancha debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="dfd30-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dfd30-136">Cuando se define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="dfd30-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="dfd30-137">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="dfd30-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="dfd30-138">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="dfd30-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="dfd30-139">Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dfd30-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dfd30-140">Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="dfd30-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfd30-141">Véase también</span><span class="sxs-lookup"><span data-stu-id="dfd30-141">See Also</span></span>

[<span data-ttu-id="dfd30-142">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="dfd30-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dfd30-143">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="dfd30-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dfd30-144">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="dfd30-145">Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="dfd30-146">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dfd30-147">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="dfd30-148">Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dfd30-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dfd30-149">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfd30-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)