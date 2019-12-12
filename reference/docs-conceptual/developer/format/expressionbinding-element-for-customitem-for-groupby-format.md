---
title: Elemento ExpressionBinding para CustomItem para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368634"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Elemento ExpressionBinding para CustomItem for GroupBy (formato)

Define los datos que muestra el control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para GroupBy (Format) elemento ExpressionBinding para CustomItem para GroupBy (Format)

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
|[Elemento CustomControlName para ExpressionBinding para GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de las colecciones.|
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se utilice este control.|
|[Elemento PropertyName para ExpressionBinding para GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor muestra el control.|
|[Elemento ScriptBlock para ExpressionBinding para GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el script cuyo valor muestra el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Define qué datos se muestran en la vista de control personalizada y cómo se muestran.|

## <a name="see-also"></a>Véase también

[Elemento CustomControlName para ExpressionBinding para GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName para ExpressionBinding para GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Elemento ScriptBlock para ExpressionBinding para GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
