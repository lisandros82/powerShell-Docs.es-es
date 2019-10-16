---
title: Elemento TableHeaders (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361824"
---
# <a name="tableheaders-element-format"></a>Elemento TableHeaders (formato)

Define los encabezados de las columnas de una tabla.

Elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `TableHeaders`. Debe haber un elemento secundario para cada propiedad del objeto que se va a mostrar. La información del encabezado de columna se muestra en el orden en que se especifican los elementos secundarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Elemento opcional.<br /><br /> Define la etiqueta, el ancho y la alineación de los datos de una columna de una vista de tabla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Tablecontrol ((Format)](./tablecontrol-element-format.md)|Define un formato de tabla para una vista.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `TableHeaders` que define dos encabezados de columna.

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

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Elemento Tablecontrol ((Format)](./tablecontrol-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
