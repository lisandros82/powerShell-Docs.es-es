---
title: Elemento de bloque de script para ItemSelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860951"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>Elemento ScriptBlock para ItemSelectionCondition for GroupBy (formato)

Especifica la secuencia de comandos que desencadena la condición. Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado de elemento de CustomItem GroupBy (formato) para CustomEntry GroupBy (formato) ExpressionBinding elemento para CustomItem para GroupBy (formato) (elemento) ItemSelectionCondition para ExpressionBinding para elemento de bloque de script GroupBy (formato) de ItemSelectionCondition para GroupBy (formato)

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
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Define la condición que debe existir para que este control que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elemento cuando se define la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
