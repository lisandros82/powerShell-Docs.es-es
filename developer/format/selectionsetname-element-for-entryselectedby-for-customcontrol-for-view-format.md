---
title: Elemento SelectionSetName para EntrySelectedBy para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063987"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>Elemento SelectionSetName para EntrySelectedBy for CustomControl for View (formato)

Especifica un conjunto de objetos de .NET para la entrada de la lista. No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry de vista (formato) del elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)

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
|[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada entrada de control personalizado debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.

Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas. Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).

Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para vista (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Vista de Control personalizado](./creating-custom-controls.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
