---
title: Elemento FirstLineHanging para el marco de control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054227"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineHanging para Frame for CustomControl for View (formato)

Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda. Este elemento se usa al definir una vista de control personalizado.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para elemento de marco de CustomControlView (formato) de CustomItem para el control personalizado de vista (formato) FirstLineHanging del elemento de marco para el control personalizado para la vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `FirstLineHanging` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de marco para CustomItem para el control personalizado para la vista (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.|

## <a name="text-value"></a>Valor de texto

Especifique el número de caracteres que se desean desplazar la primera línea de los datos.

## <a name="remarks"></a>Observaciones

Si se especifica este elemento, no se puede especificar el [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elemento.

## <a name="see-also"></a>Véase también

[Elemento FirstLineIndent marco para el control personalizado para la vista (formato)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de marco para CustomItem para el control personalizado para la vista (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
