---
title: Elemento EntrySelectedBy para WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363334"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Elemento EntrySelectedBy para WideEntry (formato)

Define los tipos de .NET que usan esta definición de la vista amplia o la condición que debe existir para que se use esta definición.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry (Format) elemento EntrySelectedBy para WideEntry (Format)

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
|[Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use esta definición de vista ancha.|
|[Elemento SelectionSetName para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de vista ancha.|
|[Elemento TypeName para EntrySelectedBy para WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de vista ancha.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Proporciona una definición de la vista amplia.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición de vista ancha. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o un valor de propiedad o un valor de script específicos se evalúa como `true`. Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Elemento WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName para EntrySelectedBy para WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
