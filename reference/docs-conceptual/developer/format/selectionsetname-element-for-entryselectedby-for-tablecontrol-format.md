---
title: Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368324"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionSetName para EntrySelectedBy for TableControl (formato)

Especifica un conjunto de tipos de .NET que usan esta entrada de la vista de tabla. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) EntrySelectedBy (Format) elemento SelectionSetName para EntrySelectedBy para TableRowEntry (Format)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define los tipos .NET que usan esta entrada o la condición que debe existir para que se use esta entrada.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas. Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).

Si especifica un conjunto de selección para una entrada, no puede especificar un nombre de tipo. Para obtener más información sobre cómo especificar un tipo .NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definir conjuntos de objetos para una vista](./defining-selection-sets.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
