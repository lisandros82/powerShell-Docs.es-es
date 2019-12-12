---
title: Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368394"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2baeb-102">Elemento SelectionCondition para EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2baeb-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2baeb-103">Define la condición que debe existir para usar para esta definición de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="2baeb-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="2baeb-104">No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de tabla.</span><span class="sxs-lookup"><span data-stu-id="2baeb-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="2baeb-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2baeb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2baeb-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2baeb-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2baeb-107">Attributes and Elements</span></span>

<span data-ttu-id="2baeb-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="2baeb-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2baeb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2baeb-109">Attributes</span></span>

<span data-ttu-id="2baeb-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2baeb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2baeb-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2baeb-111">Child Elements</span></span>

|<span data-ttu-id="2baeb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="2baeb-112">Element</span></span>|<span data-ttu-id="2baeb-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="2baeb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2baeb-114">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="2baeb-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2baeb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2baeb-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2baeb-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2baeb-117">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2baeb-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2baeb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2baeb-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2baeb-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2baeb-120">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2baeb-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2baeb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2baeb-122">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="2baeb-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="2baeb-123">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2baeb-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2baeb-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2baeb-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2baeb-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2baeb-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2baeb-126">Parent Elements</span></span>

|<span data-ttu-id="2baeb-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="2baeb-127">Element</span></span>|<span data-ttu-id="2baeb-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="2baeb-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2baeb-129">Elemento EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2baeb-130">Define los tipos .NET que usan esta entrada de tabla o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="2baeb-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2baeb-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2baeb-131">Remarks</span></span>

<span data-ttu-id="2baeb-132">Cada entrada de la lista debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="2baeb-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2baeb-133">Cuando se define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="2baeb-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2baeb-134">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2baeb-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2baeb-135">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2baeb-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2baeb-136">Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2baeb-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2baeb-137">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2baeb-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2baeb-138">Véase también</span><span class="sxs-lookup"><span data-stu-id="2baeb-138">See Also</span></span>

[<span data-ttu-id="2baeb-139">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="2baeb-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2baeb-140">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="2baeb-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2baeb-141">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2baeb-142">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="2baeb-143">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2baeb-144">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2baeb-145">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2baeb-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2baeb-146">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2baeb-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
