---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368064"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Elemento TypeName para SelectionCondition for EntrySelectedBy for WideControl (formato)

Especifica un tipo .NET que desencadena la condición. Cuando este tipo está presente, se usa la definición.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy para WideEntry (Format) elemento TypeName para SelectionCondition para EntrySelectedBy for WideEntry (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Define la condición que debe existir para que se use esta entrada ancha.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observaciones

La condición de selección puede especificar un tipo .NET o un conjunto de selección, pero no puede especificar ambos. Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista amplia](./creating-a-wide-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
