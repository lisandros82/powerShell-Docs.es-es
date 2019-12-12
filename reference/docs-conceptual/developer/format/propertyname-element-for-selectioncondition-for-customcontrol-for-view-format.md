---
title: Elemento PropertyName para SelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362354"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Elemento PropertyName para SelectionCondition for CustomControl for View (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir una vista de control personalizada.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para el elemento EntrySelectedBy de View (Format) para CustomEntry para CustomControl para el elemento SelectionCondition de View (Format) para EntrySelectedBy para CustomControl para View (Format) PropertyName Elemento para SelectionCondition para CustomControl para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Define una condición que debe existir para que se use la definición de control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad .NET.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de propiedad o un script, pero no puede especificar ambos. Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
