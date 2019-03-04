---
title: Elemento SelectionSetName para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860161"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8e34a-102">Elemento SelectionSetName para EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e34a-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8e34a-103">Especifica un conjunto de objetos de .NET para la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="8e34a-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="8e34a-104">No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="8e34a-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="8e34a-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuración para ListEntry (formato) SelectionSetName (elemento) para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8e34a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e34a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8e34a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e34a-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8e34a-107">Attributes and Elements</span></span>

<span data-ttu-id="8e34a-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8e34a-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e34a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e34a-109">Attributes</span></span>

<span data-ttu-id="8e34a-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8e34a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e34a-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8e34a-111">Child Elements</span></span>

<span data-ttu-id="8e34a-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8e34a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e34a-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8e34a-113">Parent Elements</span></span>

|<span data-ttu-id="8e34a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e34a-114">Element</span></span>|<span data-ttu-id="8e34a-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8e34a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e34a-116">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8e34a-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="8e34a-117">Define los tipos de .NET que usan esta entrada de lista o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="8e34a-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8e34a-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8e34a-118">Text Value</span></span>

<span data-ttu-id="8e34a-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="8e34a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e34a-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8e34a-120">Remarks</span></span>

<span data-ttu-id="8e34a-121">Cada entrada de la lista debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="8e34a-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8e34a-122">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="8e34a-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8e34a-123">Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="8e34a-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8e34a-124">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para obtener una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8e34a-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8e34a-125">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e34a-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e34a-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8e34a-126">Example</span></span>

<span data-ttu-id="8e34a-127">El ejemplo siguiente muestra cómo especificar una conjunto para una entrada de una vista de lista de selección.</span><span class="sxs-lookup"><span data-stu-id="8e34a-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="8e34a-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="8e34a-128">See Also</span></span>

[<span data-ttu-id="8e34a-129">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="8e34a-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8e34a-130">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8e34a-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="8e34a-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e34a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
