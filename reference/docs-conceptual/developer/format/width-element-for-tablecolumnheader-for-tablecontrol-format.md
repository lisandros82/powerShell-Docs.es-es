---
title: Elemento width para TableColumnHeader para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367874"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Width para TableColumnHeader for TableControl (formato)

Define el ancho (en caracteres) de una columna.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format) TableColumnHeader Element TableHeaders for Tablecontrol ((Format) width (elemento) para TableColumnHeader para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Width` que se usa al definir los encabezados de columna.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnHeader para TableHeaders para Tablecontrol ((Format)](./tablecolumnheader-element-format.md)|Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.|

## <a name="text-value"></a>Valor de texto

Cuando sea posible, especifique un ancho (en caracteres) mayor que la longitud de los valores de propiedad mostrados.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `TableColumnHeader` cuyo ancho es de 16 caracteres.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnHeader para TableHeader para Tablecontrol ((Format)](./tablecolumnheader-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
