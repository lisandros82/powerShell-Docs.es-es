---
title: Elemento SelectionCondition para EntrySelectedBy para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362054"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionCondition para EntrySelectedBy for Controls for View (formato)

Define una condición que debe existir para que se use la definición de control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionCondition View (Format) para EntrySelectedBy para los controles de la vista ( Aplique

## <a name="syntax"></a>Sintaxis

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para los controles de View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica una propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para los controles de View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para controles para View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para los controles de View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para controles para View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.|

## <a name="remarks"></a>Observaciones

Cuando se define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento PropertyName para SelectionCondition para los controles de View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento ScriptBlock para SelectionCondition para los controles de View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento SelectionSetName para SelectionCondition para controles para View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento TypeName para SelectionCondition para los controles de View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry para controles para View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
