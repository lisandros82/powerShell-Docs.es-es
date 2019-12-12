---
title: Elemento Frame para CustomItem para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363654"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Elemento Frame para CustomItem for Controls for View (formato)

Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles de la vista (Format) elemento CustomItem de CustomEntry para los controles del elemento de marco View (Format) para CustomItem para los controles de View (Format)

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
|[Elemento FirstLineHanging del marco de controles de la vista (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea se desplaza hacia la izquierda.|
|[Elemento FirstLineIndent del marco de controles de la vista (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea se desplaza hacia la derecha.|
|[Elemento LeftIndent del marco de controles de la vista (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.|
|[Elemento RightIndent del marco de controles de la vista (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para controles para View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define qué datos se muestran en el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) en el mismo elemento `Frame`.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging del marco de controles de la vista (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento FirstLineIndent del marco de controles de la vista (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento LeftIndent del marco de controles de la vista (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Elemento RightIndent del marco de controles de la vista (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Elemento CustomItem para CustomEntry para controles para View (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
