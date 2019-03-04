---
title: Elemento TableColumnItems para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859451"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Elemento TableColumnItems para TableRowEntry for TableControl (formato)

Define las propiedades o scripts cuyos valores se muestran en una fila.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuración (elemento) TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento TableColumnItems para TableControlEntry para TableControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableColumnItems` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItem para TableColumnItems para TableControl (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Elemento necesario.<br /><br /> Define la propiedad o el script cuyo valor se muestra en una columna de la fila.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableRowEntry para TableRowEntries para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Define los datos que se muestran en una fila de la tabla.|

## <a name="remarks"></a>Observaciones

Un `TableColumnItem` elemento es necesario para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `TableColumnItems` elemento que define tres propiedades de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

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

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
