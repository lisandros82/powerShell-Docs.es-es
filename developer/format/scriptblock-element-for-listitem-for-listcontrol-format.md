---
title: Elemento de bloque de script para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064584"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Elemento ScriptBlock para ListItem for ListControl (formato)

Especifica la secuencia de comandos cuyo valor se muestra en la fila.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntries elemento ListItems de ListControl (formato) para ListEntry elemento ListItem de ListControl (formato) para ListItems de elemento de bloque de script de ListControl (formato) de ListItem para ListControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el script cuyo valor se muestra en la fila.

## <a name="remarks"></a>Observaciones

Cuando se especifica este elemento, no puede especificar el [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.

Para obtener más información acerca de cómo especificar los scripts en una vista de lista, consulte [vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo especificar la propiedad cuyo valor se muestra.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Creación de una vista de lista](./creating-a-list-view.md)

[ListItem (elemento) para ListItems de ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
