---
title: Elemento TableColumnHeader (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361854"
---
# <a name="tablecolumnheader-element-format"></a>Elemento TableColumnHeader (formato)

Define la etiqueta, el ancho de la columna y la alineación de la etiqueta para una columna de la tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format) elemento TableColumnHeader para TableHeaders para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableColumnHeader`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Label para TableColumnHeader para Tablecontrol ((Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define la etiqueta que se muestra en la parte superior de la columna. Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.|
|[Elemento width para TableColumnHeader para Tablecontrol ((Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento obligatorio.<br /><br /> Especifica el ancho (en caracteres) de la columna.|
|[Elemento Alignment para TableColumnHeader para Tablecontrol ((Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica cómo se muestra la etiqueta de la columna. Si no se especifica ninguna alineación, la etiqueta se alinea a la izquierda.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableHeaders (Format)](./tableheaders-element-format.md)|Define las columnas de una vista de tabla.|

## <a name="remarks"></a>Observaciones

Especifique un encabezado para cada columna de la tabla. Las columnas se muestran en el orden en el que se definen los elementos `TableColumnHeader`.

Una tabla debe tener el mismo número de elementos `TableColumnHeader` que `TableRowEntry`. El encabezado de columna define cómo se muestra el texto en la parte superior de la tabla. Las entradas de fila definen qué datos se muestran en las filas de la tabla.

Para obtener más información sobre los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos elementos `TableColumnHeader`. El primer elemento define una columna cuya etiqueta es "columna 1", tiene un ancho de 16 caracteres y cuya etiqueta está alineada a la izquierda. El segundo elemento define una columna cuya etiqueta es "columna 2", tiene un ancho de 10 caracteres y cuya etiqueta está centrada en la columna.

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

[Elemento Alignment para TableColumnHeader para Tablecontrol ((Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento Label para TableColumnHeader para Tablecontrol ((Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Elemento TableHeaders para Tablecontrol ((Format)](./tableheaders-element-format.md)

[Width para TableColumnHeader para el elemento Tablecontrol ((Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
