---
title: Elemento SelectionSetName para ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076232"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Elemento SelectionSetName para ViewSelectedBy (formato)

Especifica un conjunto de objetos .NET que se muestran en la vista.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ViewSelectedBy (formato) SelectionSetName elemento de configuración ViewSelectedBy (formato)

## <a name="syntax"></a>Sintaxis

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Define los objetos de .NET que se muestran en la vista.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre del conjunto de selección que se define mediante el `Name` (elemento) para el conjunto de selección.

## <a name="remarks"></a>Observaciones

Puede usar conjuntos de selección cuando tenga un conjunto de objetos relacionados que desea hacer referencia mediante un nombre único, como un conjunto de objetos que están relacionadas mediante herencia. Para obtener más información sobre cómo definir y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo especificar una conjunto para obtener una vista de lista de selección. Se usa el mismo esquema para las vistas de tabla, amplia y personalizadas.

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

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
