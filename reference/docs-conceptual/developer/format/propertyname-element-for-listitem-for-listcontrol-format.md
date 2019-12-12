---
title: Elemento PropertyName para ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362384"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Elemento PropertyName para ListItem for ListControl (formato)

Especifica la propiedad de .NET cuyo valor se muestra en la lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento ListItems (Format) elemento ListItem (Format) PropertyName Element for ListItem (formato)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListItem (elemento, Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en la fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Cuando se especifica este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) .

Además de mostrar el valor de la propiedad, también puede especificar una etiqueta para el valor o una cadena de formato que se puede usar para cambiar la presentación del valor. Para obtener más información sobre cómo especificar datos en una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar la etiqueta y la propiedad cuyo valor se muestra.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Véase también

[Elemento ScriptBlock para ListItem para ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Elemento ListItem para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
