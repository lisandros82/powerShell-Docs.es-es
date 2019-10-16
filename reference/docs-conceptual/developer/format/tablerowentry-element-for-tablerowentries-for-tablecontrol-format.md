---
title: Elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361804"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Elemento TableRowEntry para TableRowEntries for TableControl (formato)

Define los datos que se muestran en una fila de la tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries para Tablecontrol ((Format) elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableRowEntry`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry para Tablecontrol ((Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento obligatorio.<br /><br /> Define los objetos cuyos valores de propiedad se muestran en la fila.|
|[Elemento TableColumnItems para TableRowEntry para Tablecontrol ((Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento obligatorio.<br /><br /> Define las propiedades o los scripts cuyos valores se muestran.|
|[Elemento Wrap para TableRowEntry para Tablecontrol ((Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica que el texto que supera el ancho de columna se muestra en la línea siguiente.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntries para Tablecontrol ((Format)](./tablerowentries-element-for-tablecontrol-format.md)|Define las filas de la tabla.|

## <a name="remarks"></a>Observaciones

Se debe especificar un elemento `TableColumnItems` y un elemento `EntrySelectedBy`.

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `TableRowEntry` que define una fila que muestra los valores de dos propiedades del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento EntrySelectedBy para TableRowEntry para Tablecontrol ((Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableColumnItems para TableRowEntry para Tablecontrol ((Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableRowEntries para Tablecontrol ((Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Elemento Wrap para TableRowEntry para Tablecontrol ((Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
