---
title: Elemento TableColumnItems para TableRowEntry para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361814"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Elemento TableColumnItems para TableRowEntry for TableControl (formato)

Define las propiedades o los scripts cuyos valores se muestran en una fila.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries para Tablecontrol ((Format) elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format) Elemento TableColumnItems para TableControlEntry para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableColumnItems`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItem para TableColumnItems para Tablecontrol ((Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Elemento obligatorio.<br /><br /> Define la propiedad o el script cuyo valor se muestra en una columna de la fila.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Define los datos que se muestran en una fila de la tabla.|

## <a name="remarks"></a>Observaciones

Se requiere un elemento `TableColumnItem` para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `TableColumnItems` que define tres propiedades del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Elemento TableRowEntry (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
