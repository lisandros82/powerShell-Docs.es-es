---
title: Elemento CustomItem para CustomEntry para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066388"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Elemento CustomItem para CustomEntry for Controls for View (formato)

Define qué datos se muestran el control y cómo se muestran. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de vista (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomItem` elemento. Para obtener más información, vea la sección Comentarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define los datos que se muestran el control.|
|[Elemento de marco para CustomItem para los controles de vista (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.|
|[Elemento de nueva línea para CustomItem para los controles de vista (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento de texto para CustomItem para los controles de vista (formato)](./text-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Agrega texto, como paréntesis o corchetes, a la presentación del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para los controles de vista (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Proporciona una definición del control.|

## <a name="remarks"></a>Observaciones

Al especificar los elementos secundarios de la `CustomItem` elemento, tenga en cuenta lo siguiente:

- Deben agregarse los elementos secundarios en la siguiente secuencia: `ExpressionBinding`, `NewLine`, `Text`, y `Frame`.

- No hay ningún límite máximo para el número de secuencias que se pueden especificar.

- En cada secuencia, no hay ningún límite máximo para el número de `ExpressionBinding` elementos que se pueden usar.

## <a name="see-also"></a>Véase también

[Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento de marco para CustomItem para los controles de vista (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Elemento de nueva línea para CustomItem para los controles de vista (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Elemento de texto para CustomItem para los controles de vista (formato)](./text-element-for-customitem-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
