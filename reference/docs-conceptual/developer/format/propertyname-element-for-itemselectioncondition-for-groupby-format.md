---
title: Elemento PropertyName para ItemSelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362414"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>Elemento PropertyName para ItemSelectionCondition for GroupBy (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) ItemSelectionCondition para el elemento ExpressionBinding para GroupBy (Format) PropertyName para ItemSelectionCondition para GroupBy (Format)

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
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Define la condición que debe existir para que se utilice este control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad de .NET que desencadena la condición.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
