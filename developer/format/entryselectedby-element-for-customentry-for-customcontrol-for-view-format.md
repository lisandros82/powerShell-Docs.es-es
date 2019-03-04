---
title: Elemento EntrySelectedBy para CustomEntry para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859591"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento EntrySelectedBy para CustomEntry for CustomControl for View (formato)

Define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry para vista (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que esta definición para usarse.|
|[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de la vista de control.|
|[Elemento TypeName para EntrySelectedBy para CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de la vista de control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Define los controles utilizados por objetos específicos. NET.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, el conjunto de selección o condición de selección de una entrada. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Condiciones de selección se usan para definir una condición que debe existir para la entrada que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un valor de propiedad específicos o secuencias de comandos se evalúa como `true`. Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).

Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [vista personalizada de Control](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elemento TypeName para EntrySelectedBy para CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento CustomEntry para CustomEntries para vista (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Vista de Control personalizado](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
