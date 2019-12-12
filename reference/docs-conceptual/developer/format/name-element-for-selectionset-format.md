---
title: Elemento Name para SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362674"
---
# <a name="name-element-for-selectionset-format"></a>Elemento Name para SelectionSet (formato)

Especifica el nombre usado para hacer referencia al conjunto de selección.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento Name de SelectionSet (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionSet (Format)](./selectionset-element-format.md)|Define un único conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre para hacer referencia al conjunto de selección. No hay restricciones en cuanto a los caracteres que se pueden usar.

## <a name="remarks"></a>Observaciones

El nombre especificado aquí se usa en el elemento `SelectionSetName`. Conjunto de selección que se puede usar en una vista, mediante una definición de una vista (las vistas pueden tener varias definiciones) o cuando se especifica una condición de selección. Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `SelectionSet` que define cuatro tipos .NET. El nombre del conjunto de selección es "FileSystemTypes".

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

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
