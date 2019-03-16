---
title: Elemento de ancho para TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055196"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Width para TableColumnHeader for TableControl (formato)

Define el ancho (en caracteres) de una columna.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuración TableControl (formato) elemento TableColumnHeader TableHeaders para TableControl (formato) ancho (elemento) para TableColumnHeader para TableControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `Width` elemento que se usa al definir los encabezados de columna.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.|

## <a name="text-value"></a>Valor de texto

Cuando está en todas las posibles, especifique un ancho (en caracteres) que es mayor que la longitud de los valores de propiedad que se muestra.

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `TableColumnHeader` elemento cuyo ancho es de 16 caracteres.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnHeader para TableHeader para TableControl (formato)](./tablecolumnheader-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
