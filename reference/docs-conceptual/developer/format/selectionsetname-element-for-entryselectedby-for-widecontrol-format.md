---
title: Elemento SelectionSetName para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361984"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionSetName para EntrySelectedBy for WideControl (formato)

Especifica un conjunto de objetos .NET para la definición. La definición se utiliza siempre que se muestra uno de estos objetos.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy para WideEntry (Format)

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
|[Elemento EntrySelectedBy para WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Define los tipos de .NET que usan esta entrada ancha o la condición que debe existir para que se use esta entrada.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición debe especificar un nombre de tipo, conjunto de selección o condición de selección.

Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas. Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).

Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Crear una vista amplia](./creating-a-wide-view.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento EntrySelectedBy para WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
