---
title: Elemento SelectionSetName para SelectionCondition para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368284"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento SelectionSetName para SelectionCondition for Controls for Configuration (formato)

Especifica el conjunto de tipos de .NET que desencadenan la condición. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante este control. Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.

Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para controles para Configuration (Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para controles para Configuration (Format) elemento SelectionSetName para SelectionCondition para controles de configuración (Format)

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
|[Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Define una condición que debe existir para que se use la definición de control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato. Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).

La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos. Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Definir condiciones para el momento en que se muestran los datos](./defining-conditions-for-displaying-data.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
