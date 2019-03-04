---
title: Elemento EntrySelectedBy para ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854951"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="1e990-102">Elemento EntrySelectedBy para ListEntry for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="1e990-103">Define los tipos de .NET que utilizan esta definición de vista de lista o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="1e990-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="1e990-104">En la mayoría de los casos se necesita una única definición para una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1e990-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="1e990-105">Sin embargo, puede proporcionar varias definiciones para la vista de lista si desea usar la misma vista de lista para mostrar datos diferentes para los distintos objetos.</span><span class="sxs-lookup"><span data-stu-id="1e990-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="1e990-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntry para elemento de EntrySelectedBy ListControl (formato) de ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e990-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1e990-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e990-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1e990-108">Attributes and Elements</span></span>

<span data-ttu-id="1e990-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="1e990-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e990-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e990-110">Attributes</span></span>

<span data-ttu-id="1e990-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1e990-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e990-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1e990-112">Child Elements</span></span>

|<span data-ttu-id="1e990-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e990-113">Element</span></span>|<span data-ttu-id="1e990-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="1e990-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e990-115">Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1e990-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1e990-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1e990-117">Define la condición que debe existir para que esta definición de vista de lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="1e990-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="1e990-118">Elemento SelectionSetName para EnrtySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-118">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1e990-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1e990-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1e990-120">Especifica un conjunto de tipos de .NET que usan esta definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1e990-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="1e990-121">Elemento TypeName para EntrySelectedBy de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1e990-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1e990-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1e990-123">Especifica un tipo .NET que usa esta definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1e990-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1e990-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1e990-124">Parent Elements</span></span>

|<span data-ttu-id="1e990-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e990-125">Element</span></span>|<span data-ttu-id="1e990-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="1e990-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e990-127">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="1e990-128">Define cómo se muestran las filas de la lista.</span><span class="sxs-lookup"><span data-stu-id="1e990-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e990-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1e990-129">Remarks</span></span>

<span data-ttu-id="1e990-130">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para una definición de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1e990-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="1e990-131">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="1e990-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="1e990-132">Condiciones de selección se usan para definir una condición que debe existir para que la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o que se evalúa como un valor de propiedad concreto o un script para `true`.</span><span class="sxs-lookup"><span data-stu-id="1e990-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="1e990-133">Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1e990-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1e990-134">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e990-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1e990-135">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1e990-135">Example</span></span>

<span data-ttu-id="1e990-136">El ejemplo siguiente muestra cómo se definen los objetos de una vista de lista con su nombre de tipo. NET.</span><span class="sxs-lookup"><span data-stu-id="1e990-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="1e990-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="1e990-137">See Also</span></span>

[<span data-ttu-id="1e990-138">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="1e990-139">Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1e990-140">Elemento SelectionSetName para EnrtySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-140">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1e990-141">Elemento TypeName para EntrySelectedBy de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1e990-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1e990-142">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="1e990-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1e990-143">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="1e990-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1e990-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e990-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
