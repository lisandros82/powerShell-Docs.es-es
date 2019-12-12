---
title: Elemento TypeName para tipos (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368034"
---
# <a name="typename-element-for-types-format"></a>Elemento TypeName para Types (formato)

Especifica el tipo .NET de un objeto que pertenece al conjunto de selección.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) Types (Format) elemento TypeName de Types (Format)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`. Debe incluirse al menos un elemento `TypeName` en el conjunto de selección.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Types (elemento, Format)](./types-element-for-selectionset-format.md)|Define los objetos .NET que se encuentran en el conjunto de selección.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo .NET.

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia. Al definir las vistas, puede especificar el conjunto de objetos mediante el nombre del conjunto de selección en lugar de enumerar todos los objetos de cada vista.

Los conjuntos de selección comunes se especifican por su nombre al definir las vistas del archivo de formato. En estos casos, el elemento secundario `SelectionSetName` del elemento `ViewSelectedBy` para la vista especifica el conjunto. Sin embargo, las distintas entradas de una vista también pueden especificar un conjunto de selección que se aplique solo a esa entrada de la vista. Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un elemento `SelectionSet` que define cuatro tipos .NET.

```
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

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Elemento SelectionSets (Format)](./selectionsets-element-format.md)

[Types (elemento, Format)](./types-element-for-selectionset-format.md)

[Escribir un archivo de formato de Windows PowerShell](./writing-a-powershell-formatting-file.md)
