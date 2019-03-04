---
title: Elemento de marco para CustomItem para los controles para la configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862981"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Elemento Frame para CustomItem for Controls for Configuration (formato)

Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de marco de configuración para CustomItem para los controles de configuración (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Frame` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|`CustomItem Element`|Elemento necesario|
|[Elemento FirstLineHanging marco para los controles de configuración (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.|
|[Elemento FirstLineIndent marco para los controles de configuración (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.|
|[Elemento LeftIndent marco para los controles de configuración (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.|
|[Elemento RightIndent marco para los controles de configuración (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define qué datos se muestran el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos en la misma `Frame` elemento.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging marco para los controles de configuración (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento FirstLineIndent marco para los controles de configuración (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento LeftIndent marco para los controles de configuración (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento RightIndent marco para los controles de configuración (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento CustomItem para CustomEntry para los controles de configuración](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
