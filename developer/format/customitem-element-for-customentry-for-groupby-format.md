---
title: Elemento CustomItem para CustomEntry para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856931"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Elemento CustomItem para CustomEntry for GroupBy (formato)

Define qué datos se muestran la vista de control personalizado y cómo se muestran. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomItem GroupBy (formato) para CustomEntry para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomItem` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Define los datos que se muestran el control.|
|[Elemento de marco para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Define qué datos se muestran la vista de control personalizado y cómo se muestran.|
|[Elemento de nueva línea para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica que los datos mostrados por el control de texto adicional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para el control personalizado para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Proporciona una definición de la vista de control personalizado.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para el control personalizado para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Elemento ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Elemento de marco para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[Elemento de nueva línea para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md)

[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
