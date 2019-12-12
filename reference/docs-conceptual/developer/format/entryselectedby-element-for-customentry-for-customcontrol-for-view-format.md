---
title: Elemento EntrySelectedBy para CustomEntry para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368784"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento EntrySelectedBy para CustomEntry for CustomControl for View (formato)

Define los tipos .NET que usan esta entrada personalizada o la condición que debe existir para que se use esta entrada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use esta definición.|
|[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de la vista de control.|
|[Elemento TypeName para EntrySelectedBy para CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de la vista de control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Define los controles utilizados por objetos .NET concretos.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, conjunto de selección o condición de selección para una entrada. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Las condiciones de selección se usan para definir una condición que debe existir para la entrada que se va a usar, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un script o un valor de propiedad específicos se evalúa como `true`. Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre los componentes de una vista de control personalizada, vea [vista de control personalizada](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elemento TypeName para EntrySelectedBy para CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento CustomEntry para CustomEntries para View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Vista de control personalizada](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
