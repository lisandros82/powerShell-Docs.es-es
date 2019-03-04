---
title: Elemento EntrySelectedBy para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: e18564c10898c73128e0a4bc7d077e7c7ffb1c22
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862331"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Elemento EntrySelectedBy para TableRowEntry for TableControl (formato)

Define los tipos de .NET que usan esta definición de la vista de tabla o la condición que debe existir para que esta definición para usarse.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que esta definición de vista de tabla que se usará.|
|[Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de vista de tabla.|
|[Elemento TypeName para EntrySelectedBy para TableControl (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de vista de tabla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntry para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Define los datos que se muestran en una fila de la tabla.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, el conjunto de selección o condición de selección para una definición de vista de tabla. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Condiciones de selección se usan para definir una condición que debe existir para que la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o que se evalúa como un valor de propiedad concreto o un script para `true`. Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `TableRowEntry` elemento que se utiliza para mostrar las propiedades de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

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

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TableRowEntry para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Elemento TypeName para EntrySelectedBy para TableControl (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
