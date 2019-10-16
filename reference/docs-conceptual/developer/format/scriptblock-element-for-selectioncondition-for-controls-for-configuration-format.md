---
title: Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368624"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento ScriptBlock para SelectionCondition for Controls for Configuration (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para controles de configuración (Format) Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)

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
|[Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Define una condición que debe existir para que se use la definición de control común.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos. Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
