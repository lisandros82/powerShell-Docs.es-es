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
# <a name="defining-selection-sets"></a>Definición de conjuntos de selección

Al crear varias vistas y controles, puede definir conjuntos de objetos a los que se hace referencia como conjuntos de selección. Un conjunto de selección permite definir los objetos una vez, sin tener que definirlos repetidamente para cada vista o control. Normalmente, los conjuntos de selección se usan cuando se tiene un conjunto de objetos .NET relacionados. Por ejemplo, el archivo de formato `FileSystem` (FileSystem. Format. ps1xml) define un conjunto de selección de los tipos de sistema de archivos que usan varias vistas.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Dónde se definen y se hace referencia a los conjuntos de selección

Defina los conjuntos de selección como parte de los datos comunes que se pueden usar en todas las vistas y los controles definidos en el archivo de formato. En el ejemplo siguiente se muestra cómo definir tres conjuntos de selección.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Puede hacer referencia a los conjuntos de selección de las siguientes maneras:

- Cada vista tiene un elemento `ViewSelectedBy` que define qué objetos se muestran mediante la vista. El elemento `ViewSelectedBy` tiene un `SelectionSetName` elemento secundario que especifica el conjunto de selección que usan todas las definiciones de la vista. No hay ninguna restricción en el número de conjuntos de selección a los que se puede hacer referencia desde una vista.

- En cada definición de una vista o control, el elemento `EntrySelectedBy` define qué objetos se muestran utilizando esa definición. Normalmente, una vista o un control solo tiene una definición para que los objetos se definan mediante el elemento `ViewSelectedBy`. El elemento `EntrySelectedBy` de la definición tiene un `SelectionSetName` elemento secundario que especifica el conjunto de selección. Si especifica el conjunto de selección para una definición, no puede especificar ninguno de los demás elementos secundarios del elemento `EntrySelectedBy`.

- En cada definición de una vista o control, el elemento `SelectionCondition` se puede utilizar para especificar una condición para cuando se usa la definición. El elemento `SelectionCondition` tiene un elemento secundario `SelectionSetName` que especifica el conjunto de selección que desencadena la condición. La condición se desencadena cuando se muestra cualquiera de los objetos definidos en el conjunto de selección. Para obtener más información sobre cómo establecer estas condiciones, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Ejemplo de conjunto de selección

En el ejemplo siguiente se muestra un conjunto de selección que se toma directamente del archivo de formato de `FileSystem` proporcionado por Windows PowerShell. Para obtener más información sobre otros archivos de formato de Windows PowerShell, consulte [archivos de formato de Windows PowerShell](./powershell-formatting-files.md).

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

Se hace referencia al conjunto de selección anterior en el elemento `ViewSelectedBy` de una vista de tabla.

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

## <a name="xml-elements"></a>Elementos XML

 No hay ningún límite en el número de conjuntos de selección que puede definir. Los siguientes elementos XML se utilizan para crear un conjunto de selección.

- El elemento [SelectionSets](./selectionsets-element-format.md) define los conjuntos de objetos .net a los que hacen referencia las vistas y los controles del archivo de formato.

- El elemento [SelectionSet](./selectionset-element-format.md) define un único conjunto de objetos .net.

- El elemento [Name](./name-element-for-selectionset-format.md) especifica el nombre que se usa para hacer referencia al conjunto de selección.

- El elemento [Types](./types-element-for-selectionset-format.md) especifica los tipos .net de los objetos del conjunto de selección. (Dentro de los archivos de formato, los objetos se especifican mediante su tipo de .NET).

 Los siguientes elementos XML se utilizan para especificar un conjunto de selección.

- El siguiente elemento especifica el conjunto de selección que se va a usar en todas las definiciones de la vista:

    - [Elemento SelectionSetName para ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Los elementos siguientes especifican el conjunto de selección que se usa en una definición de vista única:

    - [Elemento SelectionSetName para EntrySelectedBy para ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para CustomControl para View (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Los elementos siguientes especifican el conjunto de selección que usan las definiciones de controles de vista y comunes:

    - [Elemento SelectionSetName para EntrySelectedBy para controles para View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Los elementos siguientes especifican el conjunto de selección que se usa al definir el objeto que se va a expandir:

    - [Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Los elementos siguientes especifican el conjunto de selección que usan las condiciones de selección.

    - [Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Elemento SelectionSetName para SelectionCondition para controles para View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Elemento SelectionSetName para SelectionCondition para CustomControl para View (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Elemento SelectionSetName para SelectionCondition para GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Véase también

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nombre](./name-element-for-selectionset-format.md)

[Tipos](./types-element-for-selectionset-format.md)

[Archivos de formato de PowerShell](./powershell-formatting-files.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato y tipos de PowerShell](./writing-a-powershell-formatting-file.md)
