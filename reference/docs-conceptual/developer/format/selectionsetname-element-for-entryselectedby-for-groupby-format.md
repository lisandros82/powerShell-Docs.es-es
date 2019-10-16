---
title: Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364744"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>Elemento SelectionSetName para EntrySelectedBy for GroupBy (formato)

Especifica un conjunto de objetos .NET para la entrada de la lista. No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada. Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.

Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)

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
|[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Define los tipos .NET que usan esta entrada personalizada o la condición que debe existir para que se use esta entrada.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición de control personalizado debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.

Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas. Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

Para obtener más información sobre los componentes de una vista de control personalizada, vea [crear controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Crear controles personalizados](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
