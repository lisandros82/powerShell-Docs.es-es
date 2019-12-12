---
title: Elemento ExpressionBinding para CustomItem para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363784"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Elemento ExpressionBinding para CustomItem for Controls for View (formato)

Define los datos que muestra el control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ExpressionBinding`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|`CustomControl Element`|Elemento opcional.<br /><br /> Define un control utilizado por este control.|
|[Elemento CustomControlName para ExpressionBinding para controles para View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para controles para View (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de las colecciones.|
|[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se utilice este control.|
|[Elemento PropertyName para ExpressionBinding para los controles de View (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor muestra el control.|
|[Elemento ScriptBlock para ExpressionBinding para los controles de View (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el script cuyo valor muestra el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para controles para View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define qué datos se muestran en el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomItem para CustomEntry para controles para View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para controles para View (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento EnumerateCollection para ExpressionBinding para controles para View (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento PropertyName para ExpressionBinding para los controles de View (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ScriptBlock para ExpressionBinding para los controles de View (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
