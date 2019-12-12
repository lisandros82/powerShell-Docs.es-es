---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362014"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionCondition para EntrySelectedBy for EnumerableExpansion (formato)

Define la condición que debe existir para expandir los objetos de colección de esta definición.

Elemento de configuración (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy para EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (formato)

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

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`. Debe especificar un único `PropertyName` o un elemento `ScriptBlock`. Los elementos `SelectionSetName` y `TypeName` son opcionales. Puede especificar uno de los dos elementos.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica la propiedad de .NET que desencadena la condición.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica el script que desencadena la condición.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica el conjunto de tipos de .NET que desencadena la condición.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que desencadena la condición.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Define qué objetos de colección .NET se expanden mediante esta definición.|

## <a name="remarks"></a>Observaciones

Cada definición debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definida.

Cuando se define una condición de selección, se aplican los requisitos siguientes:

- La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para la reproducción de datos](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre otros componentes de una vista amplia, vea [vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
