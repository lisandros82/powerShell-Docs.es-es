---
title: Definir condiciones para Mostrar datos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363904"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="43169-102">Definición de condiciones para mostrar datos</span><span class="sxs-lookup"><span data-stu-id="43169-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="43169-103">Al definir los datos que se muestran en una vista o un control, puede especificar una condición que debe existir para que se muestren los datos.</span><span class="sxs-lookup"><span data-stu-id="43169-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="43169-104">La condición se puede desencadenar mediante una propiedad específica o cuando un valor de propiedad o script se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="43169-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="43169-105">Cuando se cumple la condición de selección, se utiliza la definición de la vista o el control.</span><span class="sxs-lookup"><span data-stu-id="43169-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="43169-106">Especificar una condición de selección para una definición</span><span class="sxs-lookup"><span data-stu-id="43169-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="43169-107">Al crear una definición para una vista o un control, el elemento `EntrySelectedBy` se utiliza para especificar qué objetos usarán la definición o qué condición debe existir para que se use la definición.</span><span class="sxs-lookup"><span data-stu-id="43169-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="43169-108">La condición se especifica mediante el elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="43169-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="43169-109">En el ejemplo siguiente, se especifica una condición de selección para una definición de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="43169-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="43169-110">En este ejemplo, la definición se usa solo cuando el script especificado se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="43169-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="43169-111">No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de una vista o un control.</span><span class="sxs-lookup"><span data-stu-id="43169-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="43169-112">Los únicos requisitos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="43169-112">The only requirements are the following:</span></span>

- <span data-ttu-id="43169-113">La condición de selección debe especificar un nombre de propiedad o un script para desencadenar la condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="43169-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="43169-114">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="43169-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="43169-115">Especificar una condición de selección para un elemento</span><span class="sxs-lookup"><span data-stu-id="43169-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="43169-116">También puede especificar Cuándo se utiliza un elemento de una vista de lista o un control incluyendo el elemento `ItemSelectionCondition` en la definición del elemento.</span><span class="sxs-lookup"><span data-stu-id="43169-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="43169-117">En el ejemplo siguiente, se especifica una condición de selección para un elemento de una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="43169-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="43169-118">En este ejemplo, el elemento solo se usa cuando el script se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="43169-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="43169-119">Solo puede especificar una condición de selección para un elemento.</span><span class="sxs-lookup"><span data-stu-id="43169-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="43169-120">Y la condición debe especificar un nombre de propiedad o un script para desencadenar la condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="43169-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="43169-121">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="43169-121">XML Elements</span></span>

 <span data-ttu-id="43169-122">Los siguientes elementos XML se utilizan para crear una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="43169-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="43169-123">Los elementos siguientes especifican las condiciones de selección para las definiciones de vista:</span><span class="sxs-lookup"><span data-stu-id="43169-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="43169-124">Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="43169-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="43169-125">Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="43169-126">Elemento SelectionCondition para EntrySelectedBy para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="43169-127">Elemento SelectionCondition para EntrySelectedBy para CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="43169-128">Los elementos siguientes especifican condiciones de selección para las definiciones de controles comunes y de vista:</span><span class="sxs-lookup"><span data-stu-id="43169-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="43169-129">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="43169-130">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="43169-131">El siguiente elemento especifica la condición de selección para expandir objetos de colección:</span><span class="sxs-lookup"><span data-stu-id="43169-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="43169-132">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="43169-133">El siguiente elemento especifica la condición de selección para mostrar un grupo de datos nuevo:</span><span class="sxs-lookup"><span data-stu-id="43169-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="43169-134">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="43169-135">El siguiente elemento especifica una condición de selección de elementos para una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="43169-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="43169-136">Elemento ItemSelectionCondition para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="43169-137">Los elementos siguientes especifican una condición de selección de elementos para los controles:</span><span class="sxs-lookup"><span data-stu-id="43169-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="43169-138">Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="43169-139">Elemento ItemSelectionCondition para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="43169-140">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="43169-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="43169-141">Véase también</span><span class="sxs-lookup"><span data-stu-id="43169-141">See Also</span></span>

[<span data-ttu-id="43169-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="43169-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
