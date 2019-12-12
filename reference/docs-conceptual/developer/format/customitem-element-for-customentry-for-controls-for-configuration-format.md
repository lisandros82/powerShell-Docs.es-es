---
title: Elemento CustomItem para CustomEntry para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364034"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Elemento CustomItem para CustomEntry for Controls for Configuration (formato)

Define qué datos se muestran en el control y cómo se muestran. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento CustomItem para CustomEntry para controles de configuración

## <a name="syntax"></a>Sintaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`. Para obtener más información, vea Comentarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding de CustomItem para controles de configuración (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define los datos que muestra el control.|
|[Elemento Frame para CustomItem para los controles de configuración (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.|
|[Elemento NewLine para CustomItem para los controles de configuración (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento de texto para CustomItem para los controles de configuración (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Agrega texto, como paréntesis o corchetes, a la presentación del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para los controles de configuración (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Proporciona una definición del control.|

## <a name="remarks"></a>Observaciones

Al especificar los elementos secundarios del elemento `CustomItem`, tenga en cuenta lo siguiente:

- Los elementos secundarios se deben agregar en la secuencia siguiente: `ExpressionBinding`, `NewLine`, `Text`y `Frame`.

- No hay ningún límite máximo en el número de secuencias que se pueden especificar.

- En cada secuencia, no hay ningún límite máximo para el número de elementos `ExpressionBinding` que puede usar.

## <a name="see-also"></a>Véase también

[Elemento ExpressionBinding de CustomItem para controles de configuración (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento Frame para CustomItem para los controles de configuración (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento NewLine para CustomItem para los controles de configuración (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de texto para CustomItem para los controles de configuración (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
