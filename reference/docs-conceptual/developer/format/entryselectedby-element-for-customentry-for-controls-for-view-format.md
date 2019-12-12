---
title: Elemento EntrySelectedBy para CustomEntry para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363894"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Elemento EntrySelectedBy para CustomEntry for Controls for View (formato)

Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para controles para el elemento CustomEntry de View (Format) para CustomEntries para controles para el elemento EntrySelectedBy View (Format) para CustomEntry para controles para View (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use esta definición.|
|[Elemento SelectionSetName para EntrySelectedBy para controles para View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición del control.|
|[Elemento TypeName para EntrySelectedBy para los controles de View (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Proporciona una definición del control.|

## <a name="remarks"></a>Observaciones

Las condiciones de selección se usan para definir una condición que debe existir para la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un script o un valor de propiedad específicos se evalúa como `true`. Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento CustomEntry para CustomEntries para controles para View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
