---
title: Elemento FirstLineIndent marco para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054856"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineIndent para Frame for CustomControl for View (formato)

Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha. Este elemento se usa al definir una vista de control personalizado.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para elemento de marco de CustomControlView (formato) de CustomItem para el control personalizado de vista (formato) del elemento FirstLineIndent

## <a name="syntax"></a>Sintaxis

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `FirstLineIndent` elemento.

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

Si se especifica este elemento, no se puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elemento.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para el marco de control personalizado para la vista (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de marco para CustomItem para el control personalizado para la vista (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
