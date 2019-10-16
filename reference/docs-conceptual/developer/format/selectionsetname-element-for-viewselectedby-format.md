---
title: Elemento SelectionSetName para ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368264"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Elemento SelectionSetName para ViewSelectedBy (formato)

Especifica un conjunto de objetos .NET que se muestran en la vista.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento SelectionSetName para ViewSelectedBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Define los objetos .NET que se muestran en la vista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección definido por el elemento `Name` para el conjunto de selección.

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia. Para obtener más información sobre cómo definir y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar un conjunto de selección para una vista de lista. Se usa el mismo esquema para las vistas de tabla, ancho y personalizado.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Véase también

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
