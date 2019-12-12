---
title: Elemento EntrySelectedBy para TableRowEntry para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363344"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="1ac70-102">Elemento EntrySelectedBy para TableRowEntry for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1ac70-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="1ac70-103">Define los tipos .NET que usan esta definición de la vista de tabla o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="1ac70-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="1ac70-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ac70-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1ac70-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ac70-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1ac70-106">Attributes and Elements</span></span>

<span data-ttu-id="1ac70-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="1ac70-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ac70-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ac70-108">Attributes</span></span>

<span data-ttu-id="1ac70-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1ac70-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ac70-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1ac70-110">Child Elements</span></span>

|<span data-ttu-id="1ac70-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ac70-111">Element</span></span>|<span data-ttu-id="1ac70-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="1ac70-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ac70-113">Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1ac70-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1ac70-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1ac70-115">Define la condición que debe existir para que se use esta definición de vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="1ac70-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="1ac70-116">Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1ac70-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1ac70-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1ac70-118">Especifica un conjunto de tipos de .NET que usan esta definición de vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="1ac70-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="1ac70-119">Elemento TypeName para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1ac70-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1ac70-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1ac70-121">Especifica un tipo .NET que usa esta definición de vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="1ac70-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1ac70-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1ac70-122">Parent Elements</span></span>

|<span data-ttu-id="1ac70-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ac70-123">Element</span></span>|<span data-ttu-id="1ac70-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="1ac70-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ac70-125">Elemento TableRowEntry para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="1ac70-126">Define los datos que se muestran en una fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="1ac70-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1ac70-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1ac70-127">Remarks</span></span>

<span data-ttu-id="1ac70-128">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición de vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="1ac70-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="1ac70-129">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="1ac70-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="1ac70-130">Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o que un script o un valor de propiedad específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="1ac70-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="1ac70-131">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1ac70-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1ac70-132">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1ac70-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ac70-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1ac70-133">Example</span></span>

<span data-ttu-id="1ac70-134">En el ejemplo siguiente se muestra un elemento `TableRowEntry` que se utiliza para mostrar las propiedades del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="1ac70-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="1ac70-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="1ac70-135">See Also</span></span>

[<span data-ttu-id="1ac70-136">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="1ac70-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1ac70-137">Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1ac70-138">Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1ac70-139">Elemento TableRowEntry para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="1ac70-140">Elemento TypeName para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="1ac70-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1ac70-141">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ac70-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
