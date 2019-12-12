---
title: Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364834"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>Elemento ScriptBlock para ItemSelectionCondition for GroupBy (formato)

Especifica el script que desencadena la condición. Cuando este script se evalúa como `true`, se cumple la condición y se usa el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) ItemSelectionCondition para el elemento ExpressionBinding para GroupBy (Format) elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)

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
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Define la condición que debe existir para que se utilice este control.|

## <a name="text-value"></a>Valor de texto

Especifique el script que se evalúa.

## <a name="remarks"></a>Observaciones

Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) al definir la condición de selección.

## <a name="see-also"></a>Véase también

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName para ItemSelectionCondition para GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
