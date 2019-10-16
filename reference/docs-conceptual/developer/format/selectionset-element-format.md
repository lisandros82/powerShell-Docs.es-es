---
title: Elemento SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368384"
---
# <a name="selectionset-element-format"></a>Elemento SelectionSet (formato)

Define un conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSet`. Cada conjunto de selección debe tener un nombre y debe especificar los objetos .NET del conjunto.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Name para SelectionSet (Format)](./name-element-for-selectionset-format.md)|Elemento obligatorio.<br /><br /> Especifica el nombre usado para hacer referencia al conjunto de selección.|
|[Types (elemento, Format)](./types-element-for-selectionset-format.md)|Elemento obligatorio.<br /><br /> Define los objetos .NET que se encuentran en el conjunto de selección.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Formato del elemento SelectionSets](./selectionsets-element-format.md)|Define los conjuntos comunes de objetos .NET que pueden ser utilizados por todas las vistas del archivo de formato.|

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia. Al definir las vistas, puede especificar el conjunto de objetos mediante el nombre del conjunto de selección en lugar de enumerar todos los objetos de cada vista.

Los conjuntos de selección comunes se especifican por su nombre al definir las vistas del archivo de formato o las definiciones de las vistas. En estos casos, el elemento secundario `SelectionSetName` de los elementos `ViewSelectedBy` y `EntrySelectedBy` especifica el conjunto que se va a utilizar. Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `SelectionSet` que define cuatro tipos .NET.

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Véase también

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento Name de SelectionSet (Format)](./name-element-for-selectionset-format.md)

[Elemento SelectionSets (Format)](./selectionsets-element-format.md)

[Types (elemento, Format)](./types-element-for-selectionset-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
