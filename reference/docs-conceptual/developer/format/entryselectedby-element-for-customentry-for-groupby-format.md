---
title: Elemento EntrySelectedBy para CustomEntry para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363864"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Elemento EntrySelectedBy para CustomEntry for GroupBy (formato)

Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`. Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use esta definición.|
|[Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición del control.|
|[Elemento TypeName para EntrySelectedBy para GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Proporciona una definición del control.|

## <a name="remarks"></a>Observaciones

Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un script o un valor de propiedad específicos se evalúa como `true`. Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Elemento TypeName para EntrySelectedBy para GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
