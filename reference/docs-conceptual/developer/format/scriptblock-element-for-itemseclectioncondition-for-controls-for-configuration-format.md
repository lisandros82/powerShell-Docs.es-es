---
title: Elemento ScriptBlock para ItemSeclectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362124"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Elemento ScriptBlock para ItemSelectionCondition for Controls for Configuration (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de Configuration ExpressionBinding Element for CustomItem para los controles de configuración (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format) elemento ScriptBlock para ItemSelectionCondition para controles de configuración (Format)

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
|[Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Define la condición que debe existir para que se utilice este control.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
