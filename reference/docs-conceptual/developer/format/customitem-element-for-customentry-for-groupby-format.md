---
title: Elemento CustomItem para CustomEntry para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363884"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Elemento CustomItem para CustomEntry for GroupBy (formato)

Define qué datos se muestran en la vista de control personalizada y cómo se muestran. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para GroupBy (Format)

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
|[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Define los datos que muestra el control.|
|[Elemento Frame para CustomItem para GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Define qué datos se muestran en la vista de control personalizada y cómo se muestran.|
|[Elemento NewLine para CustomItem para GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Agrega una línea en blanco a la presentación del control.|
|[Elemento Text para CustomItem para GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica texto adicional para los datos mostrados por el control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Proporciona una definición de la vista de control personalizada.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomControl para GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Elemento ExpressionBinding para CustomItem para GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Elemento Frame para CustomItem para GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Elemento NewLine para CustomItem para GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Elemento Text para CustomItem para GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
