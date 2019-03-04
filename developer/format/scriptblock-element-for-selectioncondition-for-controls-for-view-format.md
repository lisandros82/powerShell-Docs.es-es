---
title: Elemento de bloque de script para SelectionCondition para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861841"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a>Elemento ScriptBlock para SelectionCondition for Controls for View (formato)

Especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionCondition para EntrySelectedBy para los controles de vista) Elemento de bloque de script Format) para SelectionCondition para los controles de vista (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Define una condición que debe cumplirse para que se usará la definición del control.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar un nombre de la secuencia de comandos o la propiedad del uno menor para evaluar, pero no se pueden especificar ambos. Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
