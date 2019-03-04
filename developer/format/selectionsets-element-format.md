---
title: Elemento SelectionSets (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853571"
---
# <a name="selectionsets-element-format"></a>Elemento SelectionSets (formato)

Define los conjuntos comunes de objetos .NET que pueden usarse en todas las vistas del archivo de formato. Las vistas y los controles del archivo de formato pueden hacer referencia el conjunto completo de objetos utilizando únicamente el nombre del conjunto de selección.

Formato de elemento SelectionSets de elemento de configuración

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `SelectionSets` elemento. Cada elemento secundario define un conjunto de objetos que pueden hacer referencia por el nombre del conjunto. El orden de los elementos secundarios no es significativo.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Elemento necesario.<br /><br /> Define un único conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de configuración](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tenga un conjunto de objetos relacionados que desea hacer referencia mediante un nombre único, como un conjunto de objetos que están relacionadas mediante herencia. Al definir las vistas, puede especificar el conjunto de objetos con el nombre de la selección de conjunto en lugar de enumerar todos los objetos dentro de cada vista.

Al definir las vistas del archivo de formato o las definiciones de las vistas, se especifican conjuntos comunes de selección por su nombre. En estos casos, el `SelectionSetName` elemento secundario de la `ViewSelectedBy` y `EntrySelectedBy` elementos especifica el conjunto que se usará. Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="see-also"></a>Véase también

[Elemento de configuración](./configuration-element-format.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
