---
title: Elemento CustomItem para CustomEntry para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363954"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento CustomItem para CustomEntry for CustomControl for View (formato)

Define qué datos se muestran en la vista de control personalizada y cómo se muestran. Este elemento se utiliza al definir una vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para View (Format)

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

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define los datos que muestra el control.|
|[Elemento Frame para CustomItem para CustomControl para View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define qué datos se muestran en la vista de control personalizada y cómo se muestran.|
|[Elemento NewLine para CustomItem para el control personalizado de View (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento Text para CustomItem para CustomControl para View (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Elemento opcional.<br /><br /> Especifica texto adicional para los datos mostrados por el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para CustomControl para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Proporciona una definición de la vista de control personalizada.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomEntries para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento Frame para CustomItem para CustomControl para View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento NewLine para CustomItem para CustomControl para View (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento Text para CustomItem para CustomControl para View (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
