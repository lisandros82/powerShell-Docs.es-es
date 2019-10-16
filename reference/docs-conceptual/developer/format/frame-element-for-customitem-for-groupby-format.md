---
title: Elemento Frame para CustomItem para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362954"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Elemento Frame para CustomItem for GroupBy (formato)

Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para el elemento de marco GroupBy (Format) para CustomItem para GroupBy (Format)

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
|[Elemento FirstLineHanging para Frame para GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda.|
|[Elemento FirstLineIndent para Frame para GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.|
|[Elemento LeftIndent para Frame para GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.|
|[Elemento RightIndent para Frame para GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Elemento RightIndent|Elemento opcional.<br /><br /> Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Define qué datos se muestran en el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) en el mismo elemento `Frame`.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para Frame para GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento FirstLineIndent para Frame para GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento LeftIndent para Frame para GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)

[Elemento RightIndent para Frame para GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
