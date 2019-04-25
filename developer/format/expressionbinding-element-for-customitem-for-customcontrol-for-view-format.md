---
title: Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065927"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento ExpressionBinding para CustomItem for CustomControl for View (formato)

Define los datos que se muestran el control. Este elemento se usa al definir una vista de control personalizado.

Configuración (formato) elemento ViewDefinitions (formato) Vista (formato) del elemento control personalizado elemento de vista (formato) del elemento CustomEntries para el control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para el control personalizado para la vista ( Elemento de formato) CustomItem para CustomEntry para el control personalizado de vista (formato) del elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)

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
|[Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para el control personalizado para la vista (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de colecciones.|
|[Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado para la vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que este control que se usará.|
|[Elemento PropertyName para ExpressionBinding para el control personalizado para la vista (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra el control.|
|[Elemento de bloque de script para ExpressionBinding para CustomCustomControl para vista (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos cuyo valor se muestra el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para el control personalizado para la vista (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define qué datos se muestran la vista de control personalizado y cómo se muestran.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento EnumerateCollection para ExpressionBinding para el control personalizado para la vista (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado para la vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Elemento PropertyName para ExpressionBinding para el control personalizado para la vista (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento de bloque de script para ExpressionBinding para el control personalizado para la vista (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomItem para CustomEntry para el control personalizado para la vista (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
