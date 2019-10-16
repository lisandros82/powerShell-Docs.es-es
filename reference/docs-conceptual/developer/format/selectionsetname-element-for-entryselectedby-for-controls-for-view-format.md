---
title: Elemento SelectionSetName para EntrySelectedBy para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368354"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionSetName para EntrySelectedBy for Controls for View (formato)

Especifica un conjunto de tipos de .NET que usan esta definición del control. Este elemento se utiliza al definir controles que se pueden usar en una vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionSetName View (Format) para EntrySelectedBy para los controles de la vista ( Aplique

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.

### <a name="attributes"></a>Atributos

Ninguno

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para controles para View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición de control debe tener por lo menos un nombre de tipo, conjunto de selección o condición de selección definidos.

Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas. Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

## <a name="see-also"></a>Véase también

[Elemento EntrySelectedBy para CustomEntry para controles para View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
