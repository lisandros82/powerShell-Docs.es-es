---
title: Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364924"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento ScriptBlock para ItemSelectionCondition for Controls for View (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles para el elemento ScriptBlock de View (Format) para ItemSelectionCondition para controles para View (Format)

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
|[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Define la condición que debe existir para que se utilice este control.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
