---
title: Elemento Frame para CustomItem para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363644"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento Frame para CustomItem for CustomControl for View (formato)

Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir una vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para CustomControlView (Format) elemento Frame para CustomItem para CustomControl para View (Format)

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
|[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda.|
|[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.|
|[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.|
|[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define qué datos se muestran en el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) en el mismo elemento `Frame`.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento CustomItem para CustomEntry para View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
