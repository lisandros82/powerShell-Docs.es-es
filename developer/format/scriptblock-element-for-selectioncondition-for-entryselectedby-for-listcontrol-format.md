---
title: Elemento de bloque de script para SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064363"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for ListControl (formato)

Especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la entrada de la lista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuración para ListEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para elemento de bloque de script de ListEntry (formato) de SelectionCondition para EntrySelectedBy para ListEntry (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define la condición que debe existir para que esta entrada de lista para usarse.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar un nombre de la secuencia de comandos o la propiedad del uno menor para evaluar, pero no se pueden especificar ambos. (Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).)

Para obtener más información acerca de los demás componentes de una vista de lista, consulte [vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Vista de lista](./creating-a-list-view.md)

[Definir condiciones para cuando se usa un movimiento de la vista o un elemento](./defining-conditions-for-displaying-data.md)

[Escribir un formato de Windows PowerShell y los tipos de archivo](./writing-a-powershell-formatting-file.md)
