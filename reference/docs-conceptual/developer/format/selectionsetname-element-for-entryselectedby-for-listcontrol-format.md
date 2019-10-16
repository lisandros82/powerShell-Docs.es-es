---
title: Elemento SelectionSetName para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362004"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="658fb-102">Elemento SelectionSetName para EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="658fb-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="658fb-103">Especifica un conjunto de objetos .NET para la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="658fb-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="658fb-104">No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="658fb-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="658fb-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionSetName elemento for EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="658fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="658fb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="658fb-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="658fb-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="658fb-107">Attributes and Elements</span></span>

<span data-ttu-id="658fb-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="658fb-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="658fb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="658fb-109">Attributes</span></span>

<span data-ttu-id="658fb-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="658fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="658fb-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="658fb-111">Child Elements</span></span>

<span data-ttu-id="658fb-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="658fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="658fb-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="658fb-113">Parent Elements</span></span>

|<span data-ttu-id="658fb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="658fb-114">Element</span></span>|<span data-ttu-id="658fb-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="658fb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="658fb-116">Elemento EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="658fb-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="658fb-117">Define los tipos .NET que usan esta entrada de lista o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="658fb-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="658fb-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="658fb-118">Text Value</span></span>

<span data-ttu-id="658fb-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="658fb-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="658fb-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="658fb-120">Remarks</span></span>

<span data-ttu-id="658fb-121">Cada entrada de la lista debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="658fb-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="658fb-122">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="658fb-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="658fb-123">Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="658fb-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="658fb-124">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="658fb-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="658fb-125">Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="658fb-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="658fb-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="658fb-126">Example</span></span>

<span data-ttu-id="658fb-127">En el ejemplo siguiente se muestra cómo especificar un conjunto de selección para una entrada de una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="658fb-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="658fb-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="658fb-128">See Also</span></span>

[<span data-ttu-id="658fb-129">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="658fb-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="658fb-130">Elemento EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="658fb-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="658fb-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="658fb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
