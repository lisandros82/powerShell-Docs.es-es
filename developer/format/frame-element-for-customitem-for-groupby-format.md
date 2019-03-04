---
title: Elemento de marco para CustomItem para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854851"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Elemento Frame para CustomItem for GroupBy (formato)

Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para elemento de marco de GroupBy (formato) de CustomItem para GroupBy (formato)

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
|[Elemento FirstLineHanging para marco de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.|
|[Elemento FirstLineIndent marco para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.|
|[Elemento LeftIndent marco para GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.|
|[Elemento RightIndent marco para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento|Elemento opcional.<br /><br /> Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Define qué datos se muestran el control y cómo se muestran.|

## <a name="remarks"></a>Observaciones

No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementos en la misma `Frame` elemento.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para marco de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento FirstLineIndent marco para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento LeftIndent marco para GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)

[Elemento RightIndent marco para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
