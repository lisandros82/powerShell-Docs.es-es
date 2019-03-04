---
title: Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858861"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>Elemento SelectionSetName para EntrySelectedBy for GroupBy (formato)

Especifica un conjunto de objetos de .NET para la entrada de la lista. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada. Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.

Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionSetName para EntrySelectedBy para GroupBy (formato)

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
|[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición de control personalizado debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas. Por ejemplo, desea crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).

Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
