---
title: Elemento TypeName para tipos (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083797"
---
# <a name="typename-element-for-types-format"></a>Elemento TypeName para Types (formato)

Especifica el tipo de .NET de un objeto que pertenece al conjunto de selección.

Tipos de elemento SelectionSets (formato) SelectionSet elemento (formato) de configuración (formato) del elemento elemento TypeName de elemento (formato) de tipos (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento. Al menos un `TypeName` elemento debe incluirse en el conjunto de selección.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)|Define los objetos de .NET que están en la selección de conjunto.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre completo del tipo. NET.

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tenga un conjunto de objetos relacionados que desea hacer referencia mediante un nombre único, como un conjunto de objetos que están relacionadas mediante herencia. Al definir las vistas, puede especificar el conjunto de objetos con el nombre de la selección de conjunto en lugar de enumerar todos los objetos dentro de cada vista.

Al definir las vistas del archivo de formato, se especifican conjuntos comunes de selección por su nombre. En estos casos, el `SelectionSetName` elemento secundario de la `ViewSelectedBy` (elemento) para la vista especifica el conjunto. Sin embargo, las entradas diferentes de una vista también pueden especificar un conjunto de selección que se aplica solo a esa entrada de la vista. Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `SelectionSet` elemento que define cuatro tipos. NET.

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

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)

[Escribir un archivo de formato de Windows PowerShell](./writing-a-powershell-formatting-file.md)
