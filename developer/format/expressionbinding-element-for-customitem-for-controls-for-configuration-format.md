---
title: Elemento ExpressionBinding para CustomItem para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065958"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Elemento ExpressionBinding para CustomItem for Controls for Configuration (formato)

Define los datos que se muestran el control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de configuración ExpressionBinding CustomItem para los controles de configuración (formato)

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
|[Elemento CustomControlName para ExpressionBinding para los controles de configuración (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de un control común o un control de vista.|
|[Elemento EnumerateCollection para ExpressionBinding para los controles de configuración (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica que se muestran los elementos de colecciones mediante el control.|
|[Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que este control común que se usará.|
|[Elemento PropertyName para ExpressionBinding para los controles de configuración (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET cuyo valor se muestra el control común.|
|[Elemento de bloque de script para ExpressionBinding para los controles de configuración (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos cuyo valor se muestra el control común.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define qué datos se muestran la vista de control personalizado y cómo se muestran.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
