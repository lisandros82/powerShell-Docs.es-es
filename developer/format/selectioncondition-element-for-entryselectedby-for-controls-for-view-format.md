---
title: Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064250"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionCondition para EntrySelectedBy for Controls for View (formato)

Define una condición que debe cumplirse para que se usará la definición del control. Este elemento se usa al definir los controles que pueden usarse en una vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionCondition para EntrySelectedBy para los controles de vista) Formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para los controles de vista (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica una propiedad de .NET que desencadena la condición.|
|[Elemento de bloque de script para SelectionCondition para los controles de vista (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para los controles de vista (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.|

## <a name="remarks"></a>Observaciones

Al definir una condición de selección, se aplican los siguientes requisitos:

- La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.

Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento PropertyName para SelectionCondition para los controles de vista (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento de bloque de script para SelectionCondition para los controles de vista (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento TypeName para SelectionCondition para los controles de vista (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
