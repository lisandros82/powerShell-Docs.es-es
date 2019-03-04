---
title: Elemento ItemSelectionCondition para ExpressionBinding para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861851"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>Elemento ItemSelectionCondition para ExpressionBinding for Controls for View (formato)

Define la condición que debe existir para que este control que se usará. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato) Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Define los datos que se muestran el control.|

## <a name="remarks"></a>Observaciones

Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
