---
title: Definir condiciones para Mostrar datos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363904"
---
# <a name="defining-conditions-for-displaying-data"></a>Definición de condiciones para mostrar datos

Al definir los datos que se muestran en una vista o un control, puede especificar una condición que debe existir para que se muestren los datos. La condición se puede desencadenar mediante una propiedad específica o cuando un valor de propiedad o script se evalúa como `true`. Cuando se cumple la condición de selección, se utiliza la definición de la vista o el control.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Especificar una condición de selección para una definición

Al crear una definición para una vista o un control, el elemento `EntrySelectedBy` se utiliza para especificar qué objetos usarán la definición o qué condición debe existir para que se use la definición. La condición se especifica mediante el elemento `SelectionCondition`.

En el ejemplo siguiente, se especifica una condición de selección para una definición de una vista de tabla. En este ejemplo, la definición se usa solo cuando el script especificado se evalúa como `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

No hay ningún límite en el número de condiciones de selección que se pueden especificar para una definición de una vista o un control. Los únicos requisitos son los siguientes:

- La condición de selección debe especificar un nombre de propiedad o un script para desencadenar la condición, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.

## <a name="specifying-a-selection-condition-for-an-item"></a>Especificar una condición de selección para un elemento

También puede especificar Cuándo se utiliza un elemento de una vista de lista o un control incluyendo el elemento `ItemSelectionCondition` en la definición del elemento. En el ejemplo siguiente, se especifica una condición de selección para un elemento de una vista de lista. En este ejemplo, el elemento solo se usa cuando el script se evalúa como `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Solo puede especificar una condición de selección para un elemento. Y la condición debe especificar un nombre de propiedad o un script para desencadenar la condición, pero no puede especificar ambos.

## <a name="xml-elements"></a>Elementos XML

 Los siguientes elementos XML se utilizan para crear una condición de selección.

- Los elementos siguientes especifican las condiciones de selección para las definiciones de vista:

    - [Elemento SelectionCondition para EntrySelectedBy para Tablecontrol ((Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para CustomControl (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Los elementos siguientes especifican condiciones de selección para las definiciones de controles comunes y de vista:

    - [Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- El siguiente elemento especifica la condición de selección para expandir objetos de colección:

    - [Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- El siguiente elemento especifica la condición de selección para mostrar un grupo de datos nuevo:

    - [Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- El siguiente elemento especifica una condición de selección de elementos para una vista de lista:

    - [Elemento ItemSelectionCondition para ListItem para ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Los elementos siguientes especifican una condición de selección de elementos para los controles:

    - [Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Elemento ItemSelectionCondition para ExpressionBinding para controles para View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
