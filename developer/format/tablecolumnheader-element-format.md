---
title: Elemento TableColumnHeader (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858601"
---
# <a name="tablecolumnheader-element-format"></a>Elemento TableColumnHeader (formato)

Define la etiqueta, el ancho de la columna y la alineación de la etiqueta de una columna de la tabla.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuración (elemento) TableColumnHeader TableControl (formato) para TableHeaders para TableControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TableColumnHeader` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de etiqueta para TableColumnHeader para TableControl (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define la etiqueta que se muestra en la parte superior de la columna. Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.|
|[Elemento de ancho para TableColumnHeader para TableControl (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento necesario.<br /><br /> Especifica el ancho (en caracteres) de la columna.|
|[Elemento Alignment para TableColumbnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica cómo se muestra la etiqueta de la columna. Si no se especifica ninguna alineación, la etiqueta se alinea a la izquierda.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableHeaders (formato)](./tableheaders-element-format.md)|Define las columnas de una vista de tabla.|

## <a name="remarks"></a>Observaciones

Especificar un encabezado para cada columna de la tabla. Las columnas se muestran en el orden en que el `TableColumnHeader` se definen los elementos.

Una tabla debe tener el mismo número de `TableColumnHeader` elementos como `TableRowEntry` elementos. El encabezado de columna define cómo se muestra el texto en la parte superior de la tabla. Las entradas de fila definen qué datos se muestran en las filas de la tabla.

Para obtener más información acerca de los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra dos `TableColumnHeader` elementos. El primer elemento define una columna cuya etiqueta es "Columna 1", tiene un ancho de 16 caracteres, y cuya etiqueta se alinea a la izquierda. El segundo elemento define una columna cuya etiqueta es "Columna 2", tiene un ancho de 10 caracteres, y cuya etiqueta se centra en la columna.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Véase también

[Elemento Alignment para TableColumnHeader para TableContrl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento de etiqueta para TableColumnHeader para TableControl (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Elemento TableHeaders para TableControl (formato)](./tableheaders-element-format.md)

[Ancho del TableColumnHeader elemento TableControl (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
