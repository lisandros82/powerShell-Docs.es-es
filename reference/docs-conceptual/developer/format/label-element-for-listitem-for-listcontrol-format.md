---
title: Elemento Label de ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362894"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Elemento Label para ListItem for ListControl (formato)

Especifica la etiqueta que se muestra a la izquierda de la propiedad o del valor de script de la fila.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListControl (Format) ListItems para ListEntry para el elemento ListControl ( Format) elemento ListItem para ListItems para el elemento de etiqueta ListControl (Format) para ListItem para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Label`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListItem para ListItems para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique la etiqueta que se va a mostrar a la izquierda del valor de la propiedad o del script.

## <a name="remarks"></a>Observaciones

Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script. Para obtener más información sobre el uso de etiquetas en una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo agregar una etiqueta a una fila.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[ListItem (elemento, Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
