---
title: Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362074"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Elemento ScriptBlock para ItemSelectionCondition for CustomControl for View (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir una vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para View (Format) elemento ExpressionBinding para CustomItem para CustomControl para el elemento ItemSelectionCondition de View (Format) para el enlace de expresiones para CustomControl para el elemento ScriptBlock for View (Format) para ItemSelectionCondition para CustomControl para View (Format)

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
|[Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Define la condición que debe existir para que se utilice este control.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ItemSelectionCondition para CustomControl para View (Format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
