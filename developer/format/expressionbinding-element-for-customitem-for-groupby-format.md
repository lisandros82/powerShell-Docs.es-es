---
title: Elemento ExpressionBinding para CustomItem para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065910"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Elemento ExpressionBinding para CustomItem for GroupBy (formato)

Define los datos que se muestran el control. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para GroupBy (formato) (elemento) ExpressionBinding para CustomItem para GroupBy (formato)

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
|[Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection (elemento) para ExpressionBinding para GroupBy (formato)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de colecciones.|
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que este control que se usará.|
|[Elemento PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra el control.|
|[Elemento de bloque de script para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos cuyo valor se muestra el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Define qué datos se muestran la vista de control personalizado y cómo se muestran.|

## <a name="see-also"></a>Véase también

[Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Elemento de bloque de script para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
