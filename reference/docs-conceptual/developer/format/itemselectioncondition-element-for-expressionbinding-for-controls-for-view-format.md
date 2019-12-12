---
title: Elemento ItemSelectionCondition para ExpressionBinding para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362944"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>Elemento ItemSelectionCondition para ExpressionBinding for Controls for View (formato)

Define la condición que debe existir para que se utilice este control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Define los datos que muestra el control.|

## <a name="remarks"></a>Observaciones

Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
