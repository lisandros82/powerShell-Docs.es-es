---
title: Elemento PropertyName para SelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364954"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a>Elemento PropertyName para SelectionCondition for GroupBy (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento EntrySelectedBy GroupBy (Format) para CustomEntry para el elemento SelectionCondition GroupBy (Format) para EntrySelectedBy para GroupBy (Format) PropertyName para SelectionCondition para GroupBy (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Define una condición que debe existir para que se use la definición de control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad .NET.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de propiedad o un script, pero no puede especificar ambos. Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
