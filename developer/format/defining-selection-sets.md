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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858931"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="c8bb6-102">Definición de conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="c8bb6-102">Defining Selection Sets</span></span>

<span data-ttu-id="c8bb6-103">Al crear varias vistas y los controles, puede definir conjuntos de objetos que se conocen como conjuntos de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="c8bb6-104">Un conjunto de selección permite definir los objetos una vez, sin tener que definirlas repetidamente para cada vista o control.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="c8bb6-105">Normalmente, se utilizan conjuntos de selección cuando tenga un conjunto de objetos de .NET relacionados.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="c8bb6-106">Por ejemplo, el `FileSystem` el archivo de formato (FileSystem.format.ps1xml) define un conjunto de selección de los tipos de sistema de archivos que usan varias vistas.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="c8bb6-107">¿Dónde conjuntos de selección están definidos y referenciada</span><span class="sxs-lookup"><span data-stu-id="c8bb6-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="c8bb6-108">Definir conjuntos de selección como parte de los datos comunes que pueden usar todas las vistas y los controles definidos en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="c8bb6-109">El ejemplo siguiente muestra cómo se definen tres conjuntos de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="c8bb6-110">Puede hacer referencia a una selección se establece en las siguientes maneras:</span><span class="sxs-lookup"><span data-stu-id="c8bb6-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="c8bb6-111">Cada vista tiene un `ViewSelectedBy` elemento que define qué objetos se muestran mediante el uso de la vista.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="c8bb6-112">El `ViewSelectedBy` elemento tiene un `SelectionSetName` elemento secundario que especifica la selección que establece todas las definiciones de la vista de uso.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="c8bb6-113">No hay ninguna restricción en el número de conjuntos de selección que puede hacer referencia desde una vista.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="c8bb6-114">En cada definición de una vista o control, el `EntrySelectedBy` elemento define los objetos que se muestran mediante el uso de esa definición.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="c8bb6-115">Normalmente una vista o el control tiene una única definición por lo que los objetos se definen mediante la `ViewSelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="c8bb6-116">El `EntrySelectedBy` tiene el elemento de la definición de un `SelectionSetName` elemento secundario que especifica el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="c8bb6-117">Si especifica la selección definida para una definición, no se puede especificar cualquiera de los demás elementos secundarios de la `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="c8bb6-118">En cada definición de una vista o control, el `SelectionCondition` elemento puede utilizarse para especificar una condición para cuando se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="c8bb6-119">El `SelectionCondition` elemento tiene un `SelectionSetName` elemento secundario que especifica la selección de conjunto que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="c8bb6-120">La condición se desencadena cuando se muestra cualquiera de los objetos definidos en el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="c8bb6-121">Para obtener más información sobre cómo establecer estas condiciones, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c8bb6-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="c8bb6-122">Ejemplo de conjunto de selección</span><span class="sxs-lookup"><span data-stu-id="c8bb6-122">Selection Set Example</span></span>

<span data-ttu-id="c8bb6-123">El ejemplo siguiente muestra un conjunto de selección que se realiza directamente desde el `FileSystem` formato de archivo proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="c8bb6-124">Para obtener más información sobre otros PowerShell de Windows, archivos de formato, vea [archivos de formato de Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="c8bb6-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="c8bb6-125">El conjunto anterior de selección se hace referencia en el `ViewSelectedBy` elemento de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="c8bb6-126">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="c8bb6-126">XML Elements</span></span>

 <span data-ttu-id="c8bb6-127">No hay ningún límite al número de conjuntos de selección que se pueden definir.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="c8bb6-128">Los siguientes elementos XML se utilizan para crear un conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="c8bb6-129">El [SelectionSets](./selectionsets-element-format.md) elemento define los conjuntos de objetos .NET que hacen referencia las vistas y los controles del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="c8bb6-130">El [SelectionSet](./selectionset-element-format.md) elemento define un único conjunto de objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="c8bb6-131">El [nombre](./name-element-for-selectionset-format.md) elemento especifica el nombre que se usa para hacer referencia el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="c8bb6-132">El [tipos](./types-element-for-selectionset-format.md) elemento especifica los tipos de .NET de los objetos de conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="c8bb6-133">(Dentro de los archivos de formato, los objetos se especifican por su tipo. NET.)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="c8bb6-134">Los siguientes elementos XML se utilizan para especificar un conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="c8bb6-135">El elemento siguiente especifica la selección configurada para usar en todas las definiciones de la vista:</span><span class="sxs-lookup"><span data-stu-id="c8bb6-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="c8bb6-136">Elemento SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="c8bb6-137">Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="c8bb6-138">Los siguientes elementos de especifican el juego de selección que se usa una definición de vista única:</span><span class="sxs-lookup"><span data-stu-id="c8bb6-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="c8bb6-139">Elemento SelectionSetName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="c8bb6-140">Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="c8bb6-141">Elemento SelectionSetName para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="c8bb6-142">Elemento SelectionSetName para EntrySelectedBy para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="c8bb6-143">Los siguientes elementos especifican el juego de selección usa común y ver las definiciones de control:</span><span class="sxs-lookup"><span data-stu-id="c8bb6-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="c8bb6-144">Elemento SelectionSetName para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="c8bb6-145">Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="c8bb6-146">Los siguientes elementos especifican utilizado al definir el objeto para expandir el conjunto de selección:</span><span class="sxs-lookup"><span data-stu-id="c8bb6-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="c8bb6-147">Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="c8bb6-148">Los siguientes elementos especifican el conjunto de selección usando las condiciones de selección.</span><span class="sxs-lookup"><span data-stu-id="c8bb6-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="c8bb6-149">Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="c8bb6-150">Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="c8bb6-151">Elemento SelectionSetName para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="c8bb6-152">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="c8bb6-153">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="c8bb6-154">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="c8bb6-155">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="c8bb6-156">Elemento SelectionSetName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c8bb6-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="c8bb6-157">Véase también</span><span class="sxs-lookup"><span data-stu-id="c8bb6-157">See Also</span></span>

[<span data-ttu-id="c8bb6-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="c8bb6-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c8bb6-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="c8bb6-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="c8bb6-160">Name</span><span class="sxs-lookup"><span data-stu-id="c8bb6-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="c8bb6-161">Tipos de</span><span class="sxs-lookup"><span data-stu-id="c8bb6-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="c8bb6-162">Archivos de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8bb6-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="c8bb6-163">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="c8bb6-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c8bb6-164">Escribir un formato de PowerShell y el archivo de tipos</span><span class="sxs-lookup"><span data-stu-id="c8bb6-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
