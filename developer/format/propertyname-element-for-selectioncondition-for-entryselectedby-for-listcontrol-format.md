---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059021"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento PropertyName para SelectionCondition for EntrySelectedBy for ListControl (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuración para ListEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para ListEntry (formato) elemento PropertyName SelectionCondition para EntrySelectedBy para ListEntry (formato)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define la condición que debe existir para que esta entrada de lista para usarse.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de propiedad. NET.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos. Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista de lista, consulte [Crear vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[Creación de una vista de lista](./creating-a-list-view.md)

[Definir condiciones para los datos cuando se muestra.](./defining-conditions-for-displaying-data.md)

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento de bloque de script para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
