---
title: Los tipos de elemento para SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862381"
---
# <a name="types-element-for-selectionset-format"></a>Elemento Types para SelectionSet (formato)

Define los objetos de .NET que están en la selección de conjunto.

Configuración (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) los tipos de elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Types` elemento. Debe haber al menos un elemento secundario, pero no hay ningún límite máximo para el número de elementos secundarios que se pueden agregar.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TypeName de tipos (formato)](./typename-element-for-types-format.md)|Elemento necesario.<br /><br /> Especifica el objeto .NET que pertenece al conjunto de selección.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Define un conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.|

## <a name="remarks"></a>Observaciones

Los objetos definidos por este elemento constituyen un conjunto de selección que puede usar una vista, una definición de una vista (vistas pueden tener varias definiciones), o cuando se especifica una condición de selección.  Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `SelectionSet` elemento que define cuatro tipos. NET.

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

[Definición de conjuntos de objetos](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Elemento TypeName de tipos (formato)](./typename-element-for-types-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
