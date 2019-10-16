---
title: Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368394"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy for TableControl (formato)

Define la condición que debe existir para usar para esta definición de la vista de tabla. No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)

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

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento SelectionCondition.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadenan la condición.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define los tipos .NET que usan esta entrada de tabla o la condición que debe existir para que se use esta entrada.|

## <a name="remarks"></a>Observaciones

Cada entrada de la lista debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.

Cuando se define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Escribir un archivo de formato y tipos de Windows PowerShell](./writing-a-powershell-formatting-file.md)
