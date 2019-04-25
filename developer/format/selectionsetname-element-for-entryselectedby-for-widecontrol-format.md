---
title: Elemento SelectionSetName para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064040"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>Elemento SelectionSetName para EntrySelectedBy for WideControl (formato)

Especifica un conjunto de objetos de .NET para la definición. La definición se usa siempre que se muestra uno de estos objetos.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionSetName (elemento) para EntrySelectedBy para WideEntry (formato)

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
|[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Define los tipos de .NET que usan esta entrada del ancha o la condición que debe existir para que esta entrada que se usará.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Cada definición debe especificar un nombre de tipo, conjunto de selección o condición de selección.

Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas. Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos. Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir establece de objetos para obtener una vista](./defining-selection-sets.md).

Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).

## <a name="see-also"></a>Véase también

[Creación de una vista amplia](./creating-a-wide-view.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
