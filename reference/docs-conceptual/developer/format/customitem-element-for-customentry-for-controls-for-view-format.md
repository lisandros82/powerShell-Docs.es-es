---
title: Elemento CustomItem para CustomEntry para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363944"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Elemento CustomItem para CustomEntry for Controls for View (formato)

Define qué datos se muestran en el control y cómo se muestran. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para controles para el elemento CustomItem View (Format) para CustomEntry para controles para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`. Para obtener más información, vea Comentarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define los datos que muestra el control.|
|[Elemento Frame para CustomItem para los controles de View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.|
|[Elemento NewLine para CustomItem para los controles de View (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento Text para CustomItem para los controles de View (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Agrega texto, como paréntesis o corchetes, a la presentación del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Proporciona una definición del control.|

## <a name="remarks"></a>Observaciones

Al especificar los elementos secundarios del elemento `CustomItem`, tenga en cuenta lo siguiente:

- Los elementos secundarios se deben agregar en la secuencia siguiente: `ExpressionBinding`, `NewLine`, `Text`y `Frame`.

- No hay ningún límite máximo en el número de secuencias que se pueden especificar.

- En cada secuencia, no hay ningún límite máximo para el número de elementos `ExpressionBinding` que puede usar.

## <a name="see-also"></a>Véase también

[Elemento ExpressionBinding para CustomItem para controles para View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento Frame para CustomItem para los controles de View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Elemento NewLine para CustomItem para los controles de View (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Elemento Text para CustomItem para los controles de View (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
