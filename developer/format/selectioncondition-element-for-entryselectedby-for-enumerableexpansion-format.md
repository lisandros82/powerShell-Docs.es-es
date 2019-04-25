---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064142"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionCondition para EntrySelectedBy for EnumerableExpansion (formato)

Define la condición que debe existir para expandir los objetos de la colección de esta definición.

Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración (elemento) SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento. Debe especificar una sola `PropertyName` o `ScriptBlock` elemento. El `SelectionSetName` y `TypeName` elementos son opcionales. Puede especificar uno de cualquier elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento de bloque de script para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica la secuencia de comandos que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Define los objetos de colección de .NET se expanden por esta definición.|

## <a name="remarks"></a>Observaciones

Cada definición debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Al definir una condición de selección, se aplican los siguientes requisitos:

- La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.

Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para los datos de la visualización](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
