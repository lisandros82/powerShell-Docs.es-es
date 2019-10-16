---
title: Elemento Frame para CustomItem para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363664"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Elemento Frame para CustomItem for Controls for Configuration (formato)

Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para los controles de configuración (Format) elemento CustomItem para CustomEntry para controles para el elemento de marco de configuración para CustomItem para controles de configuración (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Frame`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|`CustomItem Element`|Elemento obligatorio|
|[Elemento FirstLineHanging para Frame para controles de configuración (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda.|
|[Elemento FirstLineIndent para Frame para controles de configuración (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.|
|[Elemento LeftIndent para Frame para controles de configuración (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.|
|[Elemento RightIndent para Frame para controles de configuración (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define qué datos se muestran en el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) en el mismo elemento `Frame`.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para Frame para controles de configuración (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento FirstLineIndent para Frame para controles de configuración (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento LeftIndent para Frame para controles de configuración (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento RightIndent para Frame para controles de configuración (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento CustomItem de CustomEntry para controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
