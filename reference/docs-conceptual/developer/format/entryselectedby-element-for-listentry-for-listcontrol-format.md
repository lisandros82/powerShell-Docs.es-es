---
title: Elemento EntrySelectedBy para ListEntry para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363834"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Elemento EntrySelectedBy para ListEntry for ListControl (formato)

Define los tipos de .NET que usan esta definición de vista de lista o la condición que debe existir para que se use esta definición. En la mayoría de los casos, solo se necesita una definición para una vista de lista. Sin embargo, puede proporcionar varias definiciones para la vista de lista si desea utilizar la misma vista de lista para Mostrar datos diferentes para los distintos objetos.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntry para ListControl (Format) elemento EntrySelectedBy para ListEntry para ListControl (Format)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que se use esta definición de vista de lista.|
|[Elemento SelectionSetName para EntrySelectedBy para ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de vista de lista.|
|[Elemento TypeName para EntrySelectedBy para ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListEntry para ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Define cómo se muestran las filas de la lista.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición de vista de lista. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o que un script o un valor de propiedad específicos se evalúa como `true`. Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).

Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo definir los objetos para una vista de lista utilizando su nombre de tipo .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Véase también

[Elemento ListEntry para ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName para EntrySelectedBy para ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Crear una vista de lista](./creating-a-list-view.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
