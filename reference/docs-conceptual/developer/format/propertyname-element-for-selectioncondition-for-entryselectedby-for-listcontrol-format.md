---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362294"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento PropertyName para SelectionCondition for EntrySelectedBy for ListControl (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define la condición que debe existir para que se use esta entrada de la lista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad .NET.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos. Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
