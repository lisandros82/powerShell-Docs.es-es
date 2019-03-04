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
# <a name="defining-selection-sets"></a>Definición de conjuntos de selección

Al crear varias vistas y los controles, puede definir conjuntos de objetos que se conocen como conjuntos de selección. Un conjunto de selección permite definir los objetos una vez, sin tener que definirlas repetidamente para cada vista o control. Normalmente, se utilizan conjuntos de selección cuando tenga un conjunto de objetos de .NET relacionados. Por ejemplo, el `FileSystem` el archivo de formato (FileSystem.format.ps1xml) define un conjunto de selección de los tipos de sistema de archivos que usan varias vistas.

## <a name="where-selection-sets-are-defined-and-referenced"></a>¿Dónde conjuntos de selección están definidos y referenciada

Definir conjuntos de selección como parte de los datos comunes que pueden usar todas las vistas y los controles definidos en el archivo de formato. El ejemplo siguiente muestra cómo se definen tres conjuntos de selección.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Puede hacer referencia a una selección se establece en las siguientes maneras:

- Cada vista tiene un `ViewSelectedBy` elemento que define qué objetos se muestran mediante el uso de la vista. El `ViewSelectedBy` elemento tiene un `SelectionSetName` elemento secundario que especifica la selección que establece todas las definiciones de la vista de uso. No hay ninguna restricción en el número de conjuntos de selección que puede hacer referencia desde una vista.

- En cada definición de una vista o control, el `EntrySelectedBy` elemento define los objetos que se muestran mediante el uso de esa definición. Normalmente una vista o el control tiene una única definición por lo que los objetos se definen mediante la `ViewSelectedBy` elemento. El `EntrySelectedBy` tiene el elemento de la definición de un `SelectionSetName` elemento secundario que especifica el conjunto de selección. Si especifica la selección definida para una definición, no se puede especificar cualquiera de los demás elementos secundarios de la `EntrySelectedBy` elemento.

- En cada definición de una vista o control, el `SelectionCondition` elemento puede utilizarse para especificar una condición para cuando se usa la definición. El `SelectionCondition` elemento tiene un `SelectionSetName` elemento secundario que especifica la selección de conjunto que desencadena la condición. La condición se desencadena cuando se muestra cualquiera de los objetos definidos en el conjunto de selección. Para obtener más información sobre cómo establecer estas condiciones, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Ejemplo de conjunto de selección

El ejemplo siguiente muestra un conjunto de selección que se realiza directamente desde el `FileSystem` formato de archivo proporcionado por Windows PowerShell. Para obtener más información sobre otros PowerShell de Windows, archivos de formato, vea [archivos de formato de Windows PowerShell](./powershell-formatting-files.md).

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

El conjunto anterior de selección se hace referencia en el `ViewSelectedBy` elemento de una vista de tabla.

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

 No hay ningún límite al número de conjuntos de selección que se pueden definir. Los siguientes elementos XML se utilizan para crear un conjunto de selección.

- El [SelectionSets](./selectionsets-element-format.md) elemento define los conjuntos de objetos .NET que hacen referencia las vistas y los controles del archivo de formato.

- El [SelectionSet](./selectionset-element-format.md) elemento define un único conjunto de objetos. NET.

- El [nombre](./name-element-for-selectionset-format.md) elemento especifica el nombre que se usa para hacer referencia el conjunto de selección.

- El [tipos](./types-element-for-selectionset-format.md) elemento especifica los tipos de .NET de los objetos de conjunto de selección. (Dentro de los archivos de formato, los objetos se especifican por su tipo. NET.)

 Los siguientes elementos XML se utilizan para especificar un conjunto de selección.

- El elemento siguiente especifica la selección configurada para usar en todas las definiciones de la vista:

    - [Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Los siguientes elementos de especifican el juego de selección que se usa una definición de vista única:

    - [Elemento SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para WideControl (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para el control personalizado para la vista (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Los siguientes elementos especifican el juego de selección usa común y ver las definiciones de control:

    - [Elemento SelectionSetName para EntrySelectedBy para los controles de vista (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Los siguientes elementos especifican utilizado al definir el objeto para expandir el conjunto de selección:

    - [Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Los siguientes elementos especifican el conjunto de selección usando las condiciones de selección.

    - [Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Elemento SelectionSetName para SelectionCondition para el control personalizado para la vista (formato)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Elemento SelectionSetName para SelectionCondition para GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Véase también

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Name](./name-element-for-selectionset-format.md)

[Tipos de](./types-element-for-selectionset-format.md)

[Archivos de formato de PowerShell](./powershell-formatting-files.md)

[Definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md)

[Escribir un formato de PowerShell y el archivo de tipos](./writing-a-powershell-formatting-file.md)
