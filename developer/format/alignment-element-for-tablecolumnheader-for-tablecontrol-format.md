---
title: Elemento Alignment para TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067015"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Alignment para TableColumnHeader for TableControl (formato)

Define cómo se muestran los datos en un encabezado de columna.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableHeaders (formato) elemento TableColumnHeader (formato) alineación elemento de configuración para TableColumnHeader (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `Alignment` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)|Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.|

## <a name="text-value"></a>Valor de texto

Especifique uno de los siguientes valores. Estos valores no distinguen mayúsculas de minúsculas.

Alinea a la izquierda muestran los datos en la columna de la izquierda se trata el valor predeterminado si no se especifica este elemento.

Alinea a la derecha los datos que se muestran en la columna de la derecha.

Centros de centro de los datos mostrados en la columna.

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `TableColumnHeader` elemento cuyos datos se alinean a la izquierda.

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
