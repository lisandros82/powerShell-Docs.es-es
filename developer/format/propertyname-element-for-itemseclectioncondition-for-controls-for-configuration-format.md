---
title: Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860931"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Elemento PropertyName para ItemSelectionCondition for Controls for Configuration (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de configuración ExpressionBinding CustomItem para los controles de configuración (formato) Elemento ItemSelectionCondition para ExpressionBinding para los controles de elemento de configuración (formato) PropertyName para ItemSeclectionCondition para los controles de configuración (formato)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Define la condición que debe existir para que este control que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad de .NET que desencadena la condición.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento cuando se define la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento de bloque de script para ItemSeclectionCondition para los controles de configuración (formato)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
