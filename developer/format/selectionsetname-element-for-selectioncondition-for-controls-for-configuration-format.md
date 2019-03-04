---
title: Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858141"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Elemento SelectionSetName para SelectionCondition for Controls for Configuration (formato)

Especifica el conjunto de tipos de .NET que la condición desencadenadora. Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de este control. Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.

Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para los controles para Elemento de configuración (formato) CustomEntry para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionCondition para EntrySelectedBy para los controles para Elemento de configuración (formato) SelectionSetName para SelectionCondition para los controles de configuración (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Define una condición que debe cumplirse para que se usará la definición del control.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección.

## <a name="remarks"></a>Observaciones

Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato. Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos. Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Véase también

[Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
