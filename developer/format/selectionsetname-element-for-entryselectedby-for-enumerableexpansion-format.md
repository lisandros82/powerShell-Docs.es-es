---
title: Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076266"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionSetName para EntrySelectedBy for EnumerableExpansion (formato)

Especifica el conjunto de tipos de .NET que se expanden por esta definición.

Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración (elemento) SelectionSetName EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)

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
|[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Define los objetos de colección de .NET que se expanden por esta definición.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición debe especificar uno o más nombres de tipo, un conjunto de selección o una condición de selección.

Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas. Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir establece de objetos para obtener una vista](./defining-selection-sets.md).

## <a name="see-also"></a>Véase también

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
