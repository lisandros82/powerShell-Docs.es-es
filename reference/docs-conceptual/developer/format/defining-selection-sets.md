---
title: Definir conjuntos de selección | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368854"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="2a738-102">Definición de conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="2a738-102">Defining Selection Sets</span></span>

<span data-ttu-id="2a738-103">Al crear varias vistas y controles, puede definir conjuntos de objetos a los que se hace referencia como conjuntos de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="2a738-104">Un conjunto de selección permite definir los objetos una vez, sin tener que definirlos repetidamente para cada vista o control.</span><span class="sxs-lookup"><span data-stu-id="2a738-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="2a738-105">Normalmente, los conjuntos de selección se usan cuando se tiene un conjunto de objetos .NET relacionados.</span><span class="sxs-lookup"><span data-stu-id="2a738-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="2a738-106">Por ejemplo, el archivo de formato `FileSystem` (FileSystem. Format. ps1xml) define un conjunto de selección de los tipos de sistema de archivos que usan varias vistas.</span><span class="sxs-lookup"><span data-stu-id="2a738-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="2a738-107">Dónde se definen y se hace referencia a los conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="2a738-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="2a738-108">Defina los conjuntos de selección como parte de los datos comunes que se pueden usar en todas las vistas y los controles definidos en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="2a738-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="2a738-109">En el ejemplo siguiente se muestra cómo definir tres conjuntos de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="2a738-110">Puede hacer referencia a los conjuntos de selección de las siguientes maneras:</span><span class="sxs-lookup"><span data-stu-id="2a738-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="2a738-111">Cada vista tiene un elemento `ViewSelectedBy` que define qué objetos se muestran mediante la vista.</span><span class="sxs-lookup"><span data-stu-id="2a738-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="2a738-112">El elemento `ViewSelectedBy` tiene un `SelectionSetName` elemento secundario que especifica el conjunto de selección que usan todas las definiciones de la vista.</span><span class="sxs-lookup"><span data-stu-id="2a738-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="2a738-113">No hay ninguna restricción en el número de conjuntos de selección a los que se puede hacer referencia desde una vista.</span><span class="sxs-lookup"><span data-stu-id="2a738-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="2a738-114">En cada definición de una vista o control, el elemento `EntrySelectedBy` define qué objetos se muestran utilizando esa definición.</span><span class="sxs-lookup"><span data-stu-id="2a738-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="2a738-115">Normalmente, una vista o un control solo tiene una definición para que los objetos se definan mediante el elemento `ViewSelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="2a738-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="2a738-116">El elemento `EntrySelectedBy` de la definición tiene un `SelectionSetName` elemento secundario que especifica el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="2a738-117">Si especifica el conjunto de selección para una definición, no puede especificar ninguno de los demás elementos secundarios del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="2a738-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="2a738-118">En cada definición de una vista o control, el elemento `SelectionCondition` se puede utilizar para especificar una condición para cuando se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="2a738-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="2a738-119">El elemento `SelectionCondition` tiene un elemento secundario `SelectionSetName` que especifica el conjunto de selección que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2a738-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="2a738-120">La condición se desencadena cuando se muestra cualquiera de los objetos definidos en el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="2a738-121">Para obtener más información sobre cómo establecer estas condiciones, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2a738-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="2a738-122">Ejemplo de conjunto de selección</span><span class="sxs-lookup"><span data-stu-id="2a738-122">Selection Set Example</span></span>

<span data-ttu-id="2a738-123">En el ejemplo siguiente se muestra un conjunto de selección que se toma directamente del archivo de formato de `FileSystem` proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a738-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="2a738-124">Para obtener más información sobre otros archivos de formato de Windows PowerShell, consulte [archivos de formato de Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="2a738-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="2a738-125">Se hace referencia al conjunto de selección anterior en el elemento `ViewSelectedBy` de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="2a738-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="2a738-126">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="2a738-126">XML Elements</span></span>

 <span data-ttu-id="2a738-127">No hay ningún límite en el número de conjuntos de selección que puede definir.</span><span class="sxs-lookup"><span data-stu-id="2a738-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="2a738-128">Los siguientes elementos XML se utilizan para crear un conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="2a738-129">El elemento [SelectionSets](./selectionsets-element-format.md) define los conjuntos de objetos .net a los que hacen referencia las vistas y los controles del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="2a738-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="2a738-130">El elemento [SelectionSet](./selectionset-element-format.md) define un único conjunto de objetos .net.</span><span class="sxs-lookup"><span data-stu-id="2a738-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="2a738-131">El elemento [Name](./name-element-for-selectionset-format.md) especifica el nombre que se usa para hacer referencia al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="2a738-132">El elemento [Types](./types-element-for-selectionset-format.md) especifica los tipos .net de los objetos del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="2a738-133">(Dentro de los archivos de formato, los objetos se especifican mediante su tipo de .NET).</span><span class="sxs-lookup"><span data-stu-id="2a738-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="2a738-134">Los siguientes elementos XML se utilizan para especificar un conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="2a738-135">El siguiente elemento especifica el conjunto de selección que se va a usar en todas las definiciones de la vista:</span><span class="sxs-lookup"><span data-stu-id="2a738-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="2a738-136">Elemento SelectionSetName para ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="2a738-137">Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="2a738-138">Los elementos siguientes especifican el conjunto de selección que se usa en una definición de vista única:</span><span class="sxs-lookup"><span data-stu-id="2a738-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="2a738-139">Elemento SelectionSetName para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="2a738-140">Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="2a738-141">Elemento SelectionSetName para EntrySelectedBy para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="2a738-142">Elemento SelectionSetName para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="2a738-143">Los elementos siguientes especifican el conjunto de selección que usan las definiciones de controles de vista y comunes:</span><span class="sxs-lookup"><span data-stu-id="2a738-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="2a738-144">Elemento SelectionSetName para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="2a738-145">Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="2a738-146">Los elementos siguientes especifican el conjunto de selección que se usa al definir el objeto que se va a expandir:</span><span class="sxs-lookup"><span data-stu-id="2a738-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="2a738-147">Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="2a738-148">Los elementos siguientes especifican el conjunto de selección que usan las condiciones de selección.</span><span class="sxs-lookup"><span data-stu-id="2a738-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="2a738-149">Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="2a738-150">Elemento SelectionSetName para SelectionCondition para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="2a738-151">Elemento SelectionSetName para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="2a738-152">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="2a738-153">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="2a738-154">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="2a738-155">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="2a738-156">Elemento SelectionSetName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2a738-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="2a738-157">Véase también</span><span class="sxs-lookup"><span data-stu-id="2a738-157">See Also</span></span>

[<span data-ttu-id="2a738-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="2a738-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="2a738-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="2a738-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2a738-160">Nombre</span><span class="sxs-lookup"><span data-stu-id="2a738-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="2a738-161">Tipos</span><span class="sxs-lookup"><span data-stu-id="2a738-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="2a738-162">Archivos de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a738-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="2a738-163">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="2a738-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2a738-164">Escribir un archivo de formato y tipos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a738-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
