---
title: Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368434"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>Elemento SelectionCondition para EntrySelectedBy for GroupBy (formato)

Define una condición que debe existir para que se use una definición de control. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)

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
|[Elemento PropertyName para SelectionCondition para GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica una propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.|

## <a name="remarks"></a>Observaciones

Cuando se define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento PropertyName para SelectionCondition para CustomControl para View (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento SelectionSetName para SelectionCondition para el control personalizado de View (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento TypeName para SelectionCondition para GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
