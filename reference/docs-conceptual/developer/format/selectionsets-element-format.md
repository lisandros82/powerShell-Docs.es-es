---
title: Elemento SelectionSets (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361874"
---
# <a name="selectionsets-element-format"></a>Elemento SelectionSets (formato)

Define los conjuntos comunes de objetos .NET que pueden ser utilizados por todas las vistas del archivo de formato. Las vistas y los controles del archivo de formato pueden hacer referencia al conjunto completo de objetos usando solo el nombre del conjunto de selección.

Formato del elemento SelectionSets de elemento de configuración

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSets`. Cada elemento secundario define un conjunto de objetos a los que se puede hacer referencia mediante el nombre del conjunto. El orden de los elementos secundarios no es significativo.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionSet (Format)](./selectionset-element-format.md)|Elemento obligatorio.<br /><br /> Define un único conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de configuración](./configuration-element-format.md)|Representa el elemento de nivel superior de un archivo de formato.|

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia. Al definir las vistas, puede especificar el conjunto de objetos mediante el nombre del conjunto de selección en lugar de enumerar todos los objetos de cada vista.

Los conjuntos de selección comunes se especifican por su nombre al definir las vistas del archivo de formato o las definiciones de las vistas. En estos casos, el elemento secundario `SelectionSetName` de los elementos `ViewSelectedBy` y `EntrySelectedBy` especifica el conjunto que se va a utilizar. Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="see-also"></a>Véase también

[Elemento de configuración](./configuration-element-format.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
