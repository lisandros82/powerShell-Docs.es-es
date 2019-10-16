---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361474"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Elemento TypeName para SelectionCondition for EntrySelectedBy for TableControl (formato)

Especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se cumple la condición y se usa la fila de la tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format) elemento TypeName para SelectionCondition for EntrySelectedBy for TableRowEntry (Format)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Define la condición que debe existir para que se use esta fila de tabla.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos. Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
