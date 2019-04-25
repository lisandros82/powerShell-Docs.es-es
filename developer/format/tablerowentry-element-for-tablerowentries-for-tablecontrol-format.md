---
title: Elemento TableRowEntry para TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075331"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Elemento TableRowEntry para TableRowEntries for TableControl (formato)

Define los datos que se muestran en una fila de la tabla.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuración (elemento) TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableRowEntry` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento necesario.<br /><br /> Define los objetos cuyos valores de propiedad se muestran en la fila.|
|[Elemento TableColumnItems para TableRowEntry para TableControl (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento necesario.<br /><br /> Define las propiedades o scripts cuyos valores se muestran.|
|[Ajuste el elemento para TableRowEntry para TableControl (formato)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica que el texto que supera el ancho de columna se muestra en la línea siguiente.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntries para TableControl (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Define las filas de la tabla.|

## <a name="remarks"></a>Observaciones

Una `TableColumnItems` y un elemento `EntrySelectedBy` debe especificarse el elemento.

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `TableRowEntry` elemento que define una fila que muestra los valores de las dos propiedades de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

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

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableColumnItems para TableRowEntry para TableControl (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableRowEntries para TableControl (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Ajuste el elemento para TableRowEntry para TableControl (formato)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
