---
title: Elemento SelectionCondition para EntrySelectedBy para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362054"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="f82a2-102">Elemento SelectionCondition para EntrySelectedBy for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="f82a2-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="f82a2-103">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="f82a2-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="f82a2-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="f82a2-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f82a2-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionCondition View (Format) para EntrySelectedBy para los controles de la vista ( Aplique</span><span class="sxs-lookup"><span data-stu-id="f82a2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f82a2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f82a2-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f82a2-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f82a2-107">Attributes and Elements</span></span>

<span data-ttu-id="f82a2-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="f82a2-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f82a2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f82a2-109">Attributes</span></span>

<span data-ttu-id="f82a2-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f82a2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f82a2-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f82a2-111">Child Elements</span></span>

|<span data-ttu-id="f82a2-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f82a2-112">Element</span></span>|<span data-ttu-id="f82a2-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="f82a2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f82a2-114">Elemento PropertyName para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f82a2-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f82a2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f82a2-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f82a2-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f82a2-117">Elemento ScriptBlock para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f82a2-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f82a2-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f82a2-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f82a2-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f82a2-120">Elemento SelectionSetName para SelectionCondition para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f82a2-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f82a2-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f82a2-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f82a2-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f82a2-123">Elemento TypeName para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f82a2-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f82a2-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f82a2-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f82a2-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f82a2-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f82a2-126">Parent Elements</span></span>

|<span data-ttu-id="f82a2-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="f82a2-127">Element</span></span>|<span data-ttu-id="f82a2-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="f82a2-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f82a2-129">Elemento EntrySelectedBy para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f82a2-130">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="f82a2-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f82a2-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f82a2-131">Remarks</span></span>

<span data-ttu-id="f82a2-132">Cuando se define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f82a2-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f82a2-133">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f82a2-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f82a2-134">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f82a2-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f82a2-135">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f82a2-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f82a2-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="f82a2-136">See Also</span></span>

[<span data-ttu-id="f82a2-137">Elemento PropertyName para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f82a2-138">Elemento ScriptBlock para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f82a2-139">Elemento SelectionSetName para SelectionCondition para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f82a2-140">Elemento TypeName para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f82a2-141">Elemento EntrySelectedBy para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f82a2-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f82a2-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f82a2-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
