---
title: Elemento FirstLineHanging para Frame para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363164"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineHanging para Frame for CustomControl for View (formato)

Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda. Este elemento se utiliza al definir una vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para Elemento de marco CustomEntry para CustomControlView (Format) para CustomItem para CustomControl para el elemento FirstLineHanging de View (Format) para Frame para CustomControl para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FirstLineHanging`.

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

Si se especifica este elemento, no se puede especificar el elemento [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) .

## <a name="see-also"></a>Véase también

[Elemento FirstLineIndent para Frame para CustomControl para View (Format)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento Frame para CustomItem para CustomControl para View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
