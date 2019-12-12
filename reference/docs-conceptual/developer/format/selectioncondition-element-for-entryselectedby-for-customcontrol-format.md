---
title: Elemento SelectionCondition para EntrySelectedBy para CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368444"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy for CustomControl (formato)

Define una condición que debe existir para que se use una definición de control. Este elemento se utiliza al definir una vista de control personalizada.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para el elemento EntrySelectedBy View (Format) para CustomEntry para CustomControl para el elemento SelectionCondition de View (Format) para EntrySelectedBy para CustomControl para View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para CustomControl para View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica una propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para el control personalizado de View (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para CustomControl para View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para CustomControl para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.|

## <a name="remarks"></a>Observaciones

Cuando se define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento PropertyName para SelectionCondition para CustomControl para View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento SelectionSetName para SelectionCondition para el control personalizado de View (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento TypeName para SelectionCondition para CustomControl para View (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry para CustomControl para View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
