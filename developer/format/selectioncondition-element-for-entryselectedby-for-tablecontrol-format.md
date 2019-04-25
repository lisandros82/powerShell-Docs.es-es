---
title: Elemento SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075671"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d78de-102">Elemento SelectionCondition para EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d78de-103">Define la condición que debe existir para que use para esta definición de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="d78de-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="d78de-104">No hay ningún límite al número de condiciones de selección que se pueden especificar para una definición de tabla.</span><span class="sxs-lookup"><span data-stu-id="d78de-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="d78de-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d78de-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d78de-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d78de-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d78de-107">Attributes and Elements</span></span>

<span data-ttu-id="d78de-108">Las siguientes secciones describen los atributos, elementos secundarios y el elemento primario del elemento SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="d78de-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d78de-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d78de-109">Attributes</span></span>

<span data-ttu-id="d78de-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d78de-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d78de-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d78de-111">Child Elements</span></span>

|<span data-ttu-id="d78de-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d78de-112">Element</span></span>|<span data-ttu-id="d78de-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="d78de-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d78de-114">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="d78de-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d78de-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d78de-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="d78de-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d78de-117">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d78de-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d78de-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d78de-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="d78de-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="d78de-120">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d78de-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d78de-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d78de-122">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="d78de-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="d78de-123">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d78de-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d78de-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d78de-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="d78de-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d78de-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d78de-126">Parent Elements</span></span>

|<span data-ttu-id="d78de-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="d78de-127">Element</span></span>|<span data-ttu-id="d78de-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="d78de-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d78de-129">Elemento EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d78de-130">Define los tipos de .NET que usan esta entrada de tabla o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="d78de-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d78de-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d78de-131">Remarks</span></span>

<span data-ttu-id="d78de-132">Cada entrada de la lista debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="d78de-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d78de-133">Al definir una condición de selección, se aplican los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="d78de-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d78de-134">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d78de-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d78de-135">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d78de-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d78de-136">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d78de-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d78de-137">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d78de-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d78de-138">Véase también</span><span class="sxs-lookup"><span data-stu-id="d78de-138">See Also</span></span>

[<span data-ttu-id="d78de-139">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="d78de-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d78de-140">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="d78de-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d78de-141">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d78de-142">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="d78de-143">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d78de-144">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d78de-145">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d78de-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d78de-146">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="d78de-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
