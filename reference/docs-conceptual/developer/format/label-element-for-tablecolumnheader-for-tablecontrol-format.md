---
title: Elemento Label para TableColumnHeader para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365174"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Label para TableColumnHeader for TableControl (formato)

Define la etiqueta que se muestra en la parte superior de una columna. Este elemento se utiliza al definir una vista de tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format) TableColumnHeader Element for TableHeaders for Tablecontrol ((Format) Label Element for TableColumnHeader para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Label`. Solo se permite una etiqueta para cada columna.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnHeader para TableHeaders para Tablecontrol ((Format)](./tablecolumnheader-element-format.md)|Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.|

## <a name="text-value"></a>Valor de texto

Especifique el texto que se muestra en la parte superior de la columna de la tabla. No hay caracteres restringidos para la etiqueta de columna.

## <a name="remarks"></a>Observaciones

Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `TableColumnHeader` cuya etiqueta es "Column 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
