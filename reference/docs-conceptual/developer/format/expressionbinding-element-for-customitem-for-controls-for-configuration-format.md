---
title: Elemento ExpressionBinding para CustomItem para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363194"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Elemento ExpressionBinding para CustomItem for Controls for Configuration (formato)

Define los datos que muestra el control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de Configuration ExpressionBinding Element for CustomItem para los controles de configuración (Format)

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
|[Elemento CustomControlName de ExpressionBinding para controles de configuración (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection de ExpressionBinding para controles de configuración (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica que el control muestra los elementos de las colecciones.|
|[Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se utilice este control común.|
|[Elemento PropertyName para ExpressionBinding para los controles de configuración (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra en el control común.|
|[Elemento ScriptBlock para ExpressionBinding para los controles de configuración (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el script cuyo valor muestra el control común.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define qué datos se muestran en la vista de control personalizada y cómo se muestran.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
