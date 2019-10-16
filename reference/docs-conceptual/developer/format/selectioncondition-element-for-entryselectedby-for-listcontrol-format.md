---
title: Elemento SelectionCondition para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364824"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy for ListControl (formato)

Define la condición que debe existir para usar esta definición de la vista de lista. No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format)

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
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadenan la condición.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para ListEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define los tipos .NET que usan esta entrada de tabla o la condición que debe existir para que se use esta entrada.|

## <a name="remarks"></a>Observaciones

lWhen define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName para EntrySelectedBy para ListEntry (Format)](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
