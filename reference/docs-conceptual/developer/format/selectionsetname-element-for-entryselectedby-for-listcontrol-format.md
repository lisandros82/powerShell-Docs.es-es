---
title: Elemento SelectionSetName para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362004"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>Elemento SelectionSetName para EntrySelectedBy for ListControl (formato)

Especifica un conjunto de objetos .NET para la entrada de la lista. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionSetName elemento for EntrySelectedBy para ListEntry (Format)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Define los tipos .NET que usan esta entrada de lista o la condición que debe existir para que se use esta entrada.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada entrada de la lista debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.

Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas. Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).

Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar un conjunto de selección para una entrada de una vista de lista.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Elemento EntrySelectedBy para ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
