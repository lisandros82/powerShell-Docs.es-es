---
title: Elemento SelectionSetName para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856101"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName para EntrySelectedBy for TableControl (formato)

Especifica que un conjunto de .NET tipos el uso de esta entrada de la vista de tabla. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento EntrySelectedBy (formato) SelectionSetName elemento de configuración EntrySelectedBy para TableRowEntry (formato)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las siguientes secciones describen los atributos, elementos secundarios y elementos primarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define los tipos de .NET que usan esta entrada o la condición que debe existir para que esta entrada que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas. Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para obtener una vista](./defining-selection-sets.md).

Si especifica una conjunto de selección para una entrada, no se puede especificar un nombre de tipo. Para obtener más información sobre cómo especificar un tipo. NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definición de conjuntos de objetos para obtener una vista](./defining-selection-sets.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
