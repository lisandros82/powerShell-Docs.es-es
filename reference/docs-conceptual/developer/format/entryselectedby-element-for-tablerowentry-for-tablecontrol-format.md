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
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Elemento EntrySelectedBy para TableRowEntry for TableControl (formato)

Define los tipos .NET que usan esta definición de la vista de tabla o la condición que debe existir para que se use esta definición.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use esta definición de vista de tabla.|
|[Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de vista de tabla.|
|[Elemento TypeName para EntrySelectedBy para Tablecontrol ((Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de vista de tabla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntry para Tablecontrol ((Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Define los datos que se muestran en una fila de la tabla.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición de vista de tabla. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o que un script o un valor de propiedad específicos se evalúa como `true`. Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `TableRowEntry` que se utiliza para mostrar las propiedades del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TableRowEntry para Tablecontrol ((Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Elemento TypeName para EntrySelectedBy para Tablecontrol ((Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
