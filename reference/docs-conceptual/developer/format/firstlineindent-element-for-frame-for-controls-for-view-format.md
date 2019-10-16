---
title: Elemento FirstLineIndent para Frame para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363094"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>Elemento FirstLineIndent para Frame for Controls for View (formato)

Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para controles para el elemento CustomItem de View (Format) para CustomEntry para controles para el elemento de marco View (Format) para CustomItem para los controles del elemento de marco View (Format) FirstLineIndent de Frame de controles de vista (Format)

## <a name="syntax"></a>Sintaxis

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FirstLineIndent`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Frame para CustomItem para los controles de View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.|

## <a name="text-value"></a>Valor de texto

Especifique el número de caracteres que desea desplazar la primera línea de los datos.

## <a name="remarks"></a>Observaciones

Si se especifica este elemento, no se puede especificar el elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) .

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para Frame para controles para View (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento Frame para CustomItem para los controles de View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
