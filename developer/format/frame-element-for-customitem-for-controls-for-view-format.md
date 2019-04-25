---
title: Elemento de marco para CustomItem para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065723"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Elemento Frame para CustomItem for Controls for View (formato)

Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de marco de vista (formato) para CustomItem para los controles de vista (formato)

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
|[Elemento FirstLineHanging del marco de controles de vista (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de la primera línea se desplaza a la izquierda.|
|[Elemento FirstLineIndent del marco de controles de vista (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de la primera línea se desplaza a la derecha.|
|[Elemento LeftIndent del marco de controles de vista (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.|
|[Elemento RightIndent del marco de controles de vista (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para los controles de vista (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define qué datos se muestran el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementos en la misma `Frame` elemento.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging del marco de controles de vista (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento FirstLineIndent del marco de controles de vista (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento LeftIndent del marco de controles de vista (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Elemento RightIndent del marco de controles de vista (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Elemento CustomItem para CustomEntry para los controles de vista (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
