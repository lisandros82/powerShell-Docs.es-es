---
title: Elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861161"
---
# <a name="selectionset-element-format"></a>Elemento SelectionSet (formato)

Define un conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.

Configuración (formato) elemento SelectionSets (formato) SelectionSet elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSet` elemento. Cada conjunto de selección debe tener un nombre y debe especificar los objetos de .NET del conjunto.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Name de SelectionSet (formato)](./name-element-for-selectionset-format.md)|Elemento necesario.<br /><br /> Especifica el nombre utilizado para hacer referencia el conjunto de selección.|
|[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)|Elemento necesario.<br /><br /> Define los objetos de .NET que están en la selección de conjunto.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Formato de elemento SelectionSets](./selectionsets-element-format.md)|Define los conjuntos comunes de objetos .NET que pueden usarse en todas las vistas del archivo de formato.|

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tenga un conjunto de objetos relacionados que desea hacer referencia mediante un nombre único, como un conjunto de objetos que están relacionadas mediante herencia. Al definir las vistas, puede especificar el conjunto de objetos con el nombre de la selección de conjunto en lugar de enumerar todos los objetos dentro de cada vista.

Al definir las vistas del archivo de formato o las definiciones de las vistas, se especifican conjuntos comunes de selección por su nombre. En estos casos, el `SelectionSetName` elemento secundario de la `ViewSelectedBy` y `EntrySelectedBy` elementos especifica el conjunto que se usará. Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra un `SelectionSet` elemento que define cuatro tipos. NET.

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

[Elemento Name de SelectionSet (formato)](./name-element-for-selectionset-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
