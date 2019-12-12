---
title: Elemento ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367974"
---
# <a name="viewselectedby-element-format"></a>Elemento ViewSelectedBy (formato)

Define los objetos .NET que se muestran en la vista. Cada vista debe especificar al menos un objeto .NET.

Elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format)

## <a name="syntax"></a>Sintaxis

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ViewSelectedBy`. Este elemento debe contener al menos un elemento secundario `TypeName` o `SelectionSetName`. No hay ningún límite en cuanto al número de elementos secundarios que se pueden especificar ni su orden es significativo.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TypeName para ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica un objeto .NET que se muestra en la vista.|
|[Elemento SelectionSetName para ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de objetos .NET que se muestran en la vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que muestra uno o más objetos .NET.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo se usa este elemento en diferentes vistas, vea componentes de la vista de [tabla](./creating-a-table-view.md), componentes de [vista de lista](./creating-a-list-view.md), componentes de [vista ancha](./creating-a-wide-view.md)y [componentes de control personalizados](./creating-custom-controls.md).

El elemento `SelectionSetName` se utiliza cuando el archivo de formato define un conjunto de objetos que se muestran en varias vistas. Para obtener más información sobre cómo se definen y se hace referencia a los conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo especificar el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) para una vista de lista. Se usa el mismo esquema para las vistas de tabla, ancho y personalizado.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Véase también

[Crear una vista de lista](./creating-a-list-view.md)

[Crear una vista de tabla](./creating-a-table-view.md)

[Crear una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento SelectionSetName para ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName (elemento, Format)](./typename-element-for-viewselectedby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
