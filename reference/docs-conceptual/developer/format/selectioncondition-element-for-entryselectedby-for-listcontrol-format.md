---
title: Elemento SelectionCondition para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417540"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="b8667-102">Elemento SelectionCondition para EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b8667-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="b8667-103">Define la condición que debe existir para usar esta definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b8667-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="b8667-104">No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de lista.</span><span class="sxs-lookup"><span data-stu-id="b8667-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="b8667-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8667-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b8667-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8667-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b8667-107">Attributes and Elements</span></span>

<span data-ttu-id="b8667-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="b8667-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8667-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8667-109">Attributes</span></span>

<span data-ttu-id="b8667-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b8667-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8667-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b8667-111">Child Elements</span></span>

|<span data-ttu-id="b8667-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8667-112">Element</span></span>|<span data-ttu-id="b8667-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="b8667-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8667-114">Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b8667-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b8667-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b8667-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b8667-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b8667-117">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b8667-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b8667-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b8667-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b8667-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b8667-120">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="b8667-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b8667-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b8667-122">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="b8667-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="b8667-123">Elemento TypeName para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b8667-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b8667-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b8667-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b8667-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8667-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b8667-126">Parent Elements</span></span>

|<span data-ttu-id="b8667-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8667-127">Element</span></span>|<span data-ttu-id="b8667-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="b8667-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8667-129">Elemento EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b8667-130">Define los tipos .NET que usan esta entrada de tabla o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="b8667-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8667-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b8667-131">Remarks</span></span>

<span data-ttu-id="b8667-132">lWhen define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b8667-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b8667-133">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b8667-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b8667-134">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b8667-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b8667-135">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b8667-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b8667-136">Para obtener más información sobre otros componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b8667-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8667-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="b8667-137">See Also</span></span>

[<span data-ttu-id="b8667-138">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="b8667-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b8667-139">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="b8667-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b8667-140">ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b8667-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="b8667-141">Elemento SelectionSetName para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b8667-142">Elemento TypeName para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8667-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="b8667-143">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8667-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
