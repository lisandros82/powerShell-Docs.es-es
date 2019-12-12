---
title: Elemento FirstLineIndent para Frame para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363084"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>Elemento FirstLineIndent para Frame for GroupBy (formato)

Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para el elemento de marco GroupBy (Format) para CustomItem para GroupBy (Format) elemento FirstLineIndent para Frame para GroupBy (Format)

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
|[Elemento Frame para CustomItem para GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.|

## <a name="text-value"></a>Valor de texto

Especifique el número de caracteres que desea desplazar la primera línea de los datos.

## <a name="remarks"></a>Observaciones

Si se especifica este elemento, no se puede especificar el elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) .

## <a name="see-also"></a>Véase también

[Elemento FirstLineHanging para Frame para GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento Frame para CustomItem para GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
