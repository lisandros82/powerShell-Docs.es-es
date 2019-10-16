---
title: Elemento SelectionSetName para SelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368274"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Elemento SelectionSetName para SelectionCondition for CustomControl for View (formato)

Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra utilizando este control. Este elemento se utiliza al definir una vista de control personalizada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para View (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Define una condición que debe existir para que se use la definición de control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato. Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).

La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos. Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
