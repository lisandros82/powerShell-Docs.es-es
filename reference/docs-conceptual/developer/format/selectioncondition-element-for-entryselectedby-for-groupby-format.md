---
title: Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368434"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="4559b-102">Elemento SelectionCondition para EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4559b-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="4559b-103">Define una condición que debe existir para que se use una definición de control.</span><span class="sxs-lookup"><span data-stu-id="4559b-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="4559b-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="4559b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4559b-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4559b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4559b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4559b-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4559b-107">Attributes and Elements</span></span>

<span data-ttu-id="4559b-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="4559b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4559b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4559b-109">Attributes</span></span>

<span data-ttu-id="4559b-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4559b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4559b-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4559b-111">Child Elements</span></span>

|<span data-ttu-id="4559b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4559b-112">Element</span></span>|<span data-ttu-id="4559b-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="4559b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4559b-114">Elemento PropertyName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="4559b-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4559b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4559b-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="4559b-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4559b-117">Elemento ScriptBlock para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="4559b-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4559b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4559b-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="4559b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="4559b-120">Elemento SelectionSetName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="4559b-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4559b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4559b-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="4559b-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="4559b-123">Elemento TypeName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="4559b-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4559b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="4559b-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="4559b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4559b-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4559b-126">Parent Elements</span></span>

|<span data-ttu-id="4559b-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="4559b-127">Element</span></span>|<span data-ttu-id="4559b-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="4559b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4559b-129">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="4559b-130">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="4559b-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4559b-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4559b-131">Remarks</span></span>

<span data-ttu-id="4559b-132">Cuando se define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4559b-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="4559b-133">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="4559b-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="4559b-134">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="4559b-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="4559b-135">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4559b-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4559b-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="4559b-136">See Also</span></span>

[<span data-ttu-id="4559b-137">Elemento PropertyName para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4559b-138">Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4559b-139">Elemento SelectionSetName para SelectionCondition para el control personalizado de View (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4559b-140">Elemento TypeName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="4559b-141">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4559b-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="4559b-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4559b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
