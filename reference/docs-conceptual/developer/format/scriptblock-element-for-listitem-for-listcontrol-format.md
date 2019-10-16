---
title: Elemento ScriptBlock para ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364814"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Elemento ScriptBlock para ListItem for ListControl (formato)

Especifica el script cuyo valor se muestra en la fila.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntries para ListControl (Format) elemento ListItems para ListEntry para ListControl (Format) elemento ListItem para ListItems para ListControl (Format) elemento ScriptBlock para ListItem para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ListItem (elemento, Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el script cuyo valor se muestra en la fila.

## <a name="remarks"></a>Observaciones

Cuando se especifica este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .

Para obtener más información sobre cómo especificar scripts en una vista de lista, vea la [vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar la propiedad cuyo valor se muestra.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ListItem para ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Elemento ListItem para ListItems para ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
