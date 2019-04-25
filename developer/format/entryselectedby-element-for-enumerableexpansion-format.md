---
title: Elemento EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066216"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Elemento EntrySelectedBy para EnumerableExpansion (formato)

Define los tipos de .NET que usan esta definición o la condición que debe existir para que esta definición para usarse.

Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración EnumerableExpansion (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para expandir los objetos de la colección de esta definición.|
|[Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de cómo se expanden los objetos de colección.|
|[Elemento TypeName para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de cómo se expanden los objetos de colección.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Define cómo determinados de .NET de colección, los objetos se expanden cuando se muestran en una vista.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, el conjunto de selección o condición de selección para una entrada de definición. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Condiciones de selección se usan para definir una condición que debe existir para que la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o que se evalúa como un valor de propiedad concreto o un script para `true`. Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md)

[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)

[Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento TypeName para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
