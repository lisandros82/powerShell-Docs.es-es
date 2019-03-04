---
title: Elemento CustomItem para CustomEntry para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856191"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento CustomItem para CustomEntry for CustomControl for View (formato)

Define qué datos se muestran la vista de control personalizado y cómo se muestran. Este elemento se usa al definir una vista de control personalizado.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para vista (formato)

## <a name="syntax"></a>Sintaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomItem` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define los datos que se muestran el control.|
|[Elemento de marco para CustomItem para el control personalizado para la vista (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define qué datos se muestran la vista de control personalizado y cómo se muestran.|
|[Elemento de nueva línea para CustomItem para un Control personalizado para la vista (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento de texto para CustomItem para el control personalizado para la vista (formato)](./text-element-for-customitem-for-customview-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que los datos mostrados por el control de texto adicional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para el control personalizado para la vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Proporciona una definición de la vista de control personalizado.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomEntries para vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de marco para CustomItem para el control personalizado para la vista (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de nueva línea para CustomItem para el control personalizado para la vista (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de texto para CustomItem para el control personalizado para la vista (formato)](./text-element-for-customitem-for-customview-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
