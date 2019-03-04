---
title: Elemento FirstLineIndent marco para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858561"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>Elemento FirstLineIndent para Frame for GroupBy (formato)

Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para elemento de marco de GroupBy (formato) de CustomItem GroupBy (formato) FirstLineIndent elemento de marco para GroupBy (formato)

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
|[Elemento de marco para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.|

## <a name="text-value"></a>Valor de texto

Especifique el número de caracteres que se desean desplazar la primera línea de los datos.

## <a name="remarks"></a>Observaciones

Si se especifica este elemento, no se puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) elemento.

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para marco de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento de marco para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
