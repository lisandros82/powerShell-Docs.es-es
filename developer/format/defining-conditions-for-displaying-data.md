---
title: Definir condiciones para mostrar los datos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066335"
---
# <a name="defining-conditions-for-displaying-data"></a>Definición de condiciones para mostrar datos

Al definir los datos que se muestran una vista o un control, puede especificar una condición que debe existir para que los datos que se mostrará. La condición puede activarse mediante una propiedad específica, o cuando una secuencia de comandos o se evalúa como valor de propiedad `true`. Cuando se cumple la condición de selección, se utiliza la definición de la vista o control.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Especifique una condición de selección de una definición

Al crear una definición para una vista o control, el `EntrySelectedBy` elemento se usa para especificar qué objetos se usará la definición o qué condiciones deben existir para que la definición que se usará. La condición se especifica mediante el `SelectionCondition` elemento.

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

No hay ningún límite al número de condiciones de selección que se pueden especificar para una definición de una vista o control. Los únicos requisitos son los siguientes:

- La condición de selección debe especificar un nombre de propiedad o un script para la condición desencadenadora, pero no puede especificar ambos.

- La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.

## <a name="specifying-a-selection-condition-for-an-item"></a>Especifique una condición de selección de un elemento

También puede especificar cuando se usa un elemento de una vista de lista o un control mediante la inclusión de la `ItemSelectionCondition` elemento en la definición de elemento. En el ejemplo siguiente, se especifica una condición de selección de un elemento de una vista de lista. En este ejemplo, el elemento se usa solo cuando la secuencia de comandos se evalúa como `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Puede especificar la condición de selección de un único para un elemento. Y la condición debe especificar un nombre de propiedad o un script para la condición desencadenadora, pero no puede especificar ambos.

## <a name="xml-elements"></a>Elementos XML

 Los siguientes elementos XML se utilizan para crear una condición de selección.

- Los siguientes elementos especifican condiciones de selección para definiciones de vistas:

    - [Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para WideControl (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para el control personalizado (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Los siguientes elementos de selección de especificar condiciones para common y vista de control de definiciones:

    - [Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- El elemento siguiente especifica la condición de selección de expansión de objetos de colección:

    - [Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- El elemento siguiente especifica la condición de selección para mostrar un nuevo grupo de datos:

    - [Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- El elemento siguiente especifica una condición de selección de elemento para una vista de lista:

    - [Elemento ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Los elementos siguientes especifican una condición de selección de elemento para los controles:

    - [Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Elemento ItemSelectionCondition para ExpressionBinding para los controles de vista (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
