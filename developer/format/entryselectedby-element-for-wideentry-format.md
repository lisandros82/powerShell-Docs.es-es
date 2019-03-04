---
title: Elemento EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854981"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Elemento EntrySelectedBy para WideEntry (formato)

Define los tipos de .NET que usan esta definición de la vista ampliada o la condición que debe existir para que esta definición para usarse.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que esta definición de vista amplia que se usará.|
|[Elemento SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de vista ampliada.|
|[Elemento TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de vista ampliada.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Proporciona una definición de la vista ampliada.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, el conjunto de selección o condición de selección de una definición de vista ampliada. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Condiciones de selección se usan para definir una condición que debe existir para que la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o que se evalúa como un valor de propiedad concreto o un valor de secuencia de comandos para `true`. Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
