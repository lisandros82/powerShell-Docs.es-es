---
title: Elemento TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862191"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Elemento TableRowEntries para TableControl (formato)

Define las filas de la tabla.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuración TableControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableRowEntries` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntry para TableRowEntries para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Elemento necesario.<br /><br /> Define los datos que se muestran en una fila de la tabla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableControl (formato)](./tablecontrol-element-format.md)|Define un formato de tabla para obtener una vista.|

## <a name="remarks"></a>Observaciones

Debe especificar uno o varios `TableRowEntry` elementos de la vista de tabla. No hay ningún límite máximo para el número de `TableRowEntry` elementos que se pueden agregar ni su orden significativo.

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `TableRowEntries` elemento que define una fila que muestra los valores de las dos propiedades de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento TableControl (formato)](./tablecontrol-element-format.md)

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
