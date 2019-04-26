---
title: Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075858"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Elemento PropertyName para ItemSelectionCondition for Controls for View (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato) Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato) del elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)

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
|[Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Define la condición que debe existir para que este control que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad de .NET que desencadena la condición.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento cuando se define la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
