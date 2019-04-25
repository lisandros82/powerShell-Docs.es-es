---
title: Etiqueta de elemento de ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065434"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Elemento Label para ListItem for ListControl (formato)

Especifica la etiqueta que se muestra a la izquierda del valor de propiedad o un script en la fila.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListItems ListControl (formato) para ListEntry para el elemento de ListControl ( Elemento ListItem, formato) por ListItems para elemento de etiqueta de ListControl (formato) de ListItem para ListControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Label` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListItem (elemento) para ListItems de ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique la etiqueta que se van a mostrar a la izquierda del valor de propiedad o un script.

## <a name="remarks"></a>Observaciones

Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script. Para obtener más información sobre el uso de etiquetas en una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo agregar una etiqueta a una fila.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Véase también

[Creación de una vista de lista](./creating-a-list-view.md)

[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
