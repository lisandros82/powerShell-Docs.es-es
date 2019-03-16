---
title: Elemento EntrySelectedBy para ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054950"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Elemento EntrySelectedBy para ListEntry for ListControl (formato)

Define los tipos de .NET que utilizan esta definición de vista de lista o la condición que debe existir para que esta definición para usarse. En la mayoría de los casos se necesita una única definición para una vista de lista. Sin embargo, puede proporcionar varias definiciones para la vista de lista si desea usar la misma vista de lista para mostrar datos diferentes para los distintos objetos.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntry para elemento de EntrySelectedBy ListControl (formato) de ListEntry para ListControl (formato)

## <a name="syntax"></a>Sintaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define la condición que debe existir para que esta definición de vista de lista para usarse.|
|[Elemento SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de tipos de .NET que usan esta definición de vista de lista.|
|[Elemento TypeName para EntrySelectedBy de ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica un tipo .NET que usa esta definición de vista de lista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Define cómo se muestran las filas de la lista.|

## <a name="remarks"></a>Observaciones

Debe especificar al menos un tipo, el conjunto de selección o condición de selección para una definición de vista de lista. No hay ningún límite máximo para el número de elementos secundarios que puede usar.

Condiciones de selección se usan para definir una condición que debe existir para que la definición que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o que se evalúa como un valor de propiedad concreto o un script para `true`. Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).

Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo se definen los objetos de una vista de lista con su nombre de tipo. NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Véase también

[Elemento ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName para EntrySelectedBy de ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Creación de una vista de lista](./creating-a-list-view.md)

[Definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
