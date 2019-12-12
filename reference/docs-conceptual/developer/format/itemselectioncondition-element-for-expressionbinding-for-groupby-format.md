---
title: Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365294"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Elemento ItemSelectionCondition para ExpressionBinding for GroupBy (formato)

Define la condición que debe existir para que se utilice este control. No hay ningún límite en el número de condiciones de selección que se pueden especificar para un elemento de control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) ItemSelectionCondition para ExpressionBinding para GroupBy (Format)

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
|[Elemento PropertyName para ItemSelectionCondition para GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Define los datos que muestra el control.|

## <a name="remarks"></a>Observaciones

Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
