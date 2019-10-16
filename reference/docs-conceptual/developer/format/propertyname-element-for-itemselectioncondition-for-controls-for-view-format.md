---
title: Elemento PropertyName para ItemSelectionCondition para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362484"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento PropertyName para ItemSelectionCondition for Controls for View (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format) Elemento ItemSelectionCondition de ExpressionBinding para los controles del elemento PropertyName View (Format) para ItemSelectionCondition para los controles de View (Format)

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
|[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Define la condición que debe existir para que se utilice este control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad de .NET que desencadena la condición.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
