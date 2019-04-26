---
title: Etiqueta de elemento de TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065757"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Label para TableColumnHeader for TableControl (formato)

Define la etiqueta que se muestra en la parte superior de una columna. Este elemento se usa al definir una vista de tabla.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuración (elemento) TableColumnHeader TableControl (formato) para TableHeaders para el elemento de etiqueta TableControl (formato) para TableColumnHeader para TableControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Label` elemento. Se permite sólo una etiqueta para cada columna.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.|

## <a name="text-value"></a>Valor de texto

Especifique el texto que se muestra en la parte superior de la columna de la tabla. No hay ningún carácter restringido para la etiqueta de columna.

## <a name="remarks"></a>Observaciones

Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `TableColumnHeader` elemento cuya etiqueta es "Columna 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
