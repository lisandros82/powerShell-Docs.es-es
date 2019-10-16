---
title: Elemento FirstLineIndent para Frame para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363064"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineIndent para Frame for CustomControl for View (formato)

Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir una vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para CustomControlView (Format) elemento de marco para CustomItem para CustomControl para el elemento FirstLineIndent de View (Format)

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
|[Elemento Frame para CustomItem para CustomControl para View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.|

## <a name="text-value"></a>Valor de texto

Especifique el número de caracteres que desea desplazar la primera línea de los datos.

## <a name="remarks"></a>Observaciones

Si se especifica este elemento, no se puede especificar el elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) .

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para Frame para CustomControl para View (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento Frame para CustomItem para CustomControl para View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
