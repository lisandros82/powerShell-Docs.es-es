---
title: Elemento ExpressionBinding para CustomItem para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065961"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Elemento ExpressionBinding para CustomItem for Controls for View (formato)

Define los datos que se muestran el control. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ExpressionBinding` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|`CustomControl Element`|Elemento opcional.<br /><br /> Define un control que se usa este control.|
|[Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para los controles de vista (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de colecciones.|
|[Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que este control que se usará.|
|[Elemento PropertyName para ExpressionBinding para los controles de vista (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra el control.|
|[Elemento de bloque de script para ExpressionBinding para los controles de vista (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos cuyo valor se muestra el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para los controles de vista (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define qué datos se muestran el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomItem para CustomEntry para los controles de vista (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento EnumerateCollection para ExpressionBinding para los controles de vista (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento PropertyName para ExpressionBinding para los controles de vista (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento de bloque de script para ExpressionBinding para los controles de vista (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
