---
title: Elemento SelectionCondition para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364784"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy for WideControl (formato)

Define la condición que debe existir para que se use esta definición. No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de entrada ancha.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy para WideEntry (Format)

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

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`. Debe especificar un único elemento `PropertyName` o `ScriptBlock`. Los elementos `SelectionSetName` y `TypeName` son opcionales. Puede especificar uno de los dos elementos.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el bloque de script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Define los tipos de .NET que usan esta entrada ancha o la condición que debe existir para que se use esta entrada.|

## <a name="remarks"></a>Observaciones

Cada entrada ancha debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definida.

Cuando se define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista amplia](./creating-a-wide-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento EntrySelectedBy para WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
