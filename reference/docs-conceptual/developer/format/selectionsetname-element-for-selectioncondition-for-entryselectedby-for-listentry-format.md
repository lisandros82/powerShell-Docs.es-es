---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368404"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for ListEntry (formato)

Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra con esta definición de la vista de lista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define la condición que debe existir para usar esta definición de la vista de lista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos. Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato. Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).

Para obtener más información sobre otros componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
