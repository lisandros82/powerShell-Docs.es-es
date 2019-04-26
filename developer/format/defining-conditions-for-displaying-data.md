---
title: Definir condiciones para mostrar los datos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066335"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="15f43-102">Definición de condiciones para mostrar datos</span><span class="sxs-lookup"><span data-stu-id="15f43-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="15f43-103">Al definir los datos que se muestran una vista o un control, puede especificar una condición que debe existir para que los datos que se mostrará.</span><span class="sxs-lookup"><span data-stu-id="15f43-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="15f43-104">La condición puede activarse mediante una propiedad específica, o cuando una secuencia de comandos o se evalúa como valor de propiedad `true`.</span><span class="sxs-lookup"><span data-stu-id="15f43-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="15f43-105">Cuando se cumple la condición de selección, se utiliza la definición de la vista o control.</span><span class="sxs-lookup"><span data-stu-id="15f43-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="15f43-106">Especifique una condición de selección de una definición</span><span class="sxs-lookup"><span data-stu-id="15f43-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="15f43-107">Al crear una definición para una vista o control, el `EntrySelectedBy` elemento se usa para especificar qué objetos se usará la definición o qué condiciones deben existir para que la definición que se usará.</span><span class="sxs-lookup"><span data-stu-id="15f43-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="15f43-108">La condición se especifica mediante el `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="15f43-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="15f43-109">En el ejemplo siguiente, se especifica una condición de selección para una definición de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="15f43-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="15f43-110">En este ejemplo, la definición se usa solo cuando el script especificado se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="15f43-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="15f43-111">No hay ningún límite al número de condiciones de selección que se pueden especificar para una definición de una vista o control.</span><span class="sxs-lookup"><span data-stu-id="15f43-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="15f43-112">Los únicos requisitos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="15f43-112">The only requirements are the following:</span></span>

- <span data-ttu-id="15f43-113">La condición de selección debe especificar un nombre de propiedad o un script para la condición desencadenadora, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="15f43-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="15f43-114">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="15f43-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="15f43-115">Especifique una condición de selección de un elemento</span><span class="sxs-lookup"><span data-stu-id="15f43-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="15f43-116">También puede especificar cuando se usa un elemento de una vista de lista o un control mediante la inclusión de la `ItemSelectionCondition` elemento en la definición de elemento.</span><span class="sxs-lookup"><span data-stu-id="15f43-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="15f43-117">En el ejemplo siguiente, se especifica una condición de selección de un elemento de una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="15f43-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="15f43-118">En este ejemplo, el elemento se usa solo cuando la secuencia de comandos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="15f43-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="15f43-119">Puede especificar la condición de selección de un único para un elemento.</span><span class="sxs-lookup"><span data-stu-id="15f43-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="15f43-120">Y la condición debe especificar un nombre de propiedad o un script para la condición desencadenadora, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="15f43-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="15f43-121">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="15f43-121">XML Elements</span></span>

 <span data-ttu-id="15f43-122">Los siguientes elementos XML se utilizan para crear una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="15f43-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="15f43-123">Los siguientes elementos especifican condiciones de selección para definiciones de vistas:</span><span class="sxs-lookup"><span data-stu-id="15f43-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="15f43-124">Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="15f43-125">Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="15f43-126">Elemento SelectionCondition para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="15f43-127">Elemento SelectionCondition para EntrySelectedBy para el control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="15f43-128">Los siguientes elementos de selección de especificar condiciones para common y vista de control de definiciones:</span><span class="sxs-lookup"><span data-stu-id="15f43-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="15f43-129">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="15f43-130">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="15f43-131">El elemento siguiente especifica la condición de selección de expansión de objetos de colección:</span><span class="sxs-lookup"><span data-stu-id="15f43-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="15f43-132">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="15f43-133">El elemento siguiente especifica la condición de selección para mostrar un nuevo grupo de datos:</span><span class="sxs-lookup"><span data-stu-id="15f43-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="15f43-134">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="15f43-135">El elemento siguiente especifica una condición de selección de elemento para una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="15f43-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="15f43-136">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="15f43-137">Los elementos siguientes especifican una condición de selección de elemento para los controles:</span><span class="sxs-lookup"><span data-stu-id="15f43-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="15f43-138">Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="15f43-139">Elemento ItemSelectionCondition para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="15f43-140">Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="15f43-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="15f43-141">Véase también</span><span class="sxs-lookup"><span data-stu-id="15f43-141">See Also</span></span>

[<span data-ttu-id="15f43-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="15f43-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
