---
title: Elemento EntrySelectedBy para CustomEntry para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066233"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Elemento EntrySelectedBy para CustomEntry for GroupBy (formato)

Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `EntrySelectedBy` elemento. Debe especificar al menos un tipo, el conjunto de selección o condición de selección de una definición. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que esta definición para usarse.|
|[Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición del control.|
|[Elemento TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición del control.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CustomEntry para el control personalizado para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Proporciona una definición del control.|

## <a name="remarks"></a>Observaciones

Condiciones de selección se usan para definir una condición que debe existir para la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un valor de propiedad específicos o secuencias de comandos se evalúa como `true`. Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Elemento TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Elemento CustomEntry para CustomEntries para los controles de vista (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
