---
title: Nombre de elemento para SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858171"
---
# <a name="name-element-for-selectionset-format"></a>Elemento Name para SelectionSet (formato)

Especifica el nombre utilizado para hacer referencia el conjunto de selección.

Elemento SelectionSet (formato) nombre elemento de configuración (formato) del elemento elemento SelectionSets (formato) de SelectionSet (formato)

## <a name="syntax"></a>Sintaxis

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `Name` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Define un único conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre que se hacen referencia al conjunto de selección. Hay no hay restricciones en cuanto a qué caracteres se pueden usar.

## <a name="remarks"></a>Observaciones

El nombre especificado aquí se usa en el `SelectionSetName` elemento. El conjunto de selección que puede usar una vista, una definición de una vista (vistas pueden tener varias definiciones), o cuando se especifica una condición de selección. Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `SelectionSet` elemento que define cuatro tipos. NET. El nombre del conjunto de selección es "FileSystemTypes".

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

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
