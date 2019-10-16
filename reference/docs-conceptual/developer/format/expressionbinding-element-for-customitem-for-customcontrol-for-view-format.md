---
title: Elemento ExpressionBinding para CustomItem para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363154"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento ExpressionBinding para CustomItem for CustomControl for View (formato)

Define los datos que muestra el control. Este elemento se utiliza al definir una vista de control personalizada.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para la vista (Format) elemento ExpressionBinding para CustomItem para CustomControl para View (Format)

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
|[Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para CustomControl para View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de las colecciones.|
|[Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se utilice este control.|
|[Elemento PropertyName para ExpressionBinding para CustomControl para View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor muestra el control.|
|[Elemento ScriptBlock para ExpressionBinding para CustomCustomControl para View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el script cuyo valor muestra el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para CustomControl para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define qué datos se muestran en la vista de control personalizada y cómo se muestran.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento EnumerateCollection para ExpressionBinding para CustomControl para View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para View (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Elemento PropertyName para ExpressionBinding para CustomControl para View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock para ExpressionBinding para CustomControl para View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomItem para CustomEntry para CustomControl para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
