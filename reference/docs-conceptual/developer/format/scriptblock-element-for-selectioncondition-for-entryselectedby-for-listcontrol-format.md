---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368594"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for ListControl (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format) elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define la condición que debe existir para que se use esta entrada de la lista.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos. (Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para cuando se usa una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md)).

Para obtener más información sobre los demás componentes de una vista de lista, vea [vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Vista de lista](./creating-a-list-view.md)

[Definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
