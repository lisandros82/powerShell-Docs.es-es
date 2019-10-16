---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365004"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>Elemento PropertyName para SelectionCondition for EntrySelectedBy for TableRowEntry (formato)

Especifica la propiedad de .NET que desencadena la condición. Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format) NombreDePropiedad Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Define la condición que debe existir para que se use esta entrada de tabla.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad .NET.

## <a name="remarks"></a>Observaciones

La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos. Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
