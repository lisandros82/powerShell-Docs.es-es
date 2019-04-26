---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064057"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for TableControl (formato)

Especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de esta definición de la vista de tabla.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato) (elemento) SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Define la condición que debe existir para que use para esta definición de la vista de tabla.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos. Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).

Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato. Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista de tabla](./creating-a-table-view.md).

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md)

[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
