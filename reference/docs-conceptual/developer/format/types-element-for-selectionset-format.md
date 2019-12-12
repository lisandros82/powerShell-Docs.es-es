---
title: Elemento Types para SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367964"
---
# <a name="types-element-for-selectionset-format"></a>Elemento Types para SelectionSet (formato)

Define los objetos .NET que se encuentran en el conjunto de selección.

Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento Types (Format)

## <a name="syntax"></a>Sintaxis

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Types`. Debe haber al menos un elemento secundario, pero no hay ningún límite máximo para el número de elementos secundarios que se pueden agregar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TypeName de Types (Format)](./typename-element-for-types-format.md)|Elemento necesario.<br /><br /> Especifica el objeto .NET que pertenece al conjunto de selección.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionSet (Format)](./selectionset-element-format.md)|Define un conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.|

## <a name="remarks"></a>Observaciones

Los objetos definidos por este elemento componen un conjunto de selección que se puede usar en una vista, mediante una definición de una vista (las vistas pueden tener varias definiciones) o cuando se especifica una condición de selección.  Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `SelectionSet` que define cuatro tipos .NET.

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

[Definir conjuntos de objetos](./defining-selection-sets.md)

[Elemento SelectionSet (Format)](./selectionset-element-format.md)

[Elemento TypeName de Types (Format)](./typename-element-for-types-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
