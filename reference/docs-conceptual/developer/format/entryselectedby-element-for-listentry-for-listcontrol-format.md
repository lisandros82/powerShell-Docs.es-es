---
title: Elemento EntrySelectedBy para ListEntry para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363834"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="3ed54-102">Elemento EntrySelectedBy para ListEntry for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3ed54-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="3ed54-103">Define los tipos de .NET que usan esta definición de vista de lista o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="3ed54-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="3ed54-104">En la mayoría de los casos, solo se necesita una definición para una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3ed54-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="3ed54-105">Sin embargo, puede proporcionar varias definiciones para la vista de lista si desea utilizar la misma vista de lista para Mostrar datos diferentes para los distintos objetos.</span><span class="sxs-lookup"><span data-stu-id="3ed54-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="3ed54-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntry para ListControl (Format) elemento EntrySelectedBy para ListEntry para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ed54-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3ed54-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ed54-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3ed54-108">Attributes and Elements</span></span>

<span data-ttu-id="3ed54-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="3ed54-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ed54-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ed54-110">Attributes</span></span>

<span data-ttu-id="3ed54-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3ed54-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ed54-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3ed54-112">Child Elements</span></span>

|<span data-ttu-id="3ed54-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ed54-113">Element</span></span>|<span data-ttu-id="3ed54-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="3ed54-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ed54-115">Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3ed54-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ed54-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3ed54-117">Define la condición que debe existir para que se use esta definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3ed54-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="3ed54-118">Elemento SelectionSetName para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3ed54-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ed54-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3ed54-120">Especifica un conjunto de tipos de .NET que usan esta definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3ed54-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="3ed54-121">Elemento TypeName para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3ed54-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ed54-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3ed54-123">Especifica un tipo .NET que usa esta definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3ed54-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ed54-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3ed54-124">Parent Elements</span></span>

|<span data-ttu-id="3ed54-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ed54-125">Element</span></span>|<span data-ttu-id="3ed54-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="3ed54-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ed54-127">Elemento ListEntry para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="3ed54-128">Define cómo se muestran las filas de la lista.</span><span class="sxs-lookup"><span data-stu-id="3ed54-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ed54-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3ed54-129">Remarks</span></span>

<span data-ttu-id="3ed54-130">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3ed54-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="3ed54-131">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="3ed54-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="3ed54-132">Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o que un script o un valor de propiedad específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="3ed54-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="3ed54-133">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3ed54-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3ed54-134">Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3ed54-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3ed54-135">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3ed54-135">Example</span></span>

<span data-ttu-id="3ed54-136">En el ejemplo siguiente se muestra cómo definir los objetos para una vista de lista utilizando su nombre de tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="3ed54-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="3ed54-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="3ed54-137">See Also</span></span>

[<span data-ttu-id="3ed54-138">Elemento ListEntry para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="3ed54-139">Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3ed54-140">Elemento SelectionSetName para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3ed54-141">Elemento TypeName para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ed54-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3ed54-142">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="3ed54-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3ed54-143">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="3ed54-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3ed54-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ed54-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
