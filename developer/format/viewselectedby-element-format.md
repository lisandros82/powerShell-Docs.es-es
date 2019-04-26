---
title: Elemento ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083831"
---
# <a name="viewselectedby-element-format"></a>Elemento ViewSelectedBy (formato)

Define los objetos de .NET que se muestran en la vista. Cada vista debe especificar al menos un objeto. NET.

Elemento ViewDefinitions (formato) vista elemento (formato) ViewSelectedBy elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ViewSelectedBy` elemento. Este elemento debe contener al menos un `TypeName` o `SelectionSetName` elemento secundario. No hay ningún límite al número de elementos secundarios que se puede especificar ni su orden significativo.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TypeName para ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica un objeto .NET que se muestra la vista.|
|[Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica un conjunto de objetos .NET que se muestran en la vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que muestra uno o varios objetos. NET.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo se usa este elemento en distintas vistas, consulte [los componentes de vista de tabla](./creating-a-table-view.md), [los componentes de vista de lista](./creating-a-list-view.md), [los componentes de vista amplia](./creating-a-wide-view.md)y [Control personalizado componentes](./creating-custom-controls.md).

El `SelectionSetName` elemento se usa cuando el archivo de formato define un conjunto de objetos que se muestran en varias vistas. Para obtener más información acerca de cómo se definen y se hace referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo especificar el [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para obtener una vista de lista. Se usa el mismo esquema para las vistas de tabla, amplia y personalizadas.

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

[Creación de una vista de lista](./creating-a-list-view.md)

[Creación de una vista de tabla](./creating-a-table-view.md)

[Creación de una vista amplia](./creating-a-wide-view.md)

[Creación de controles personalizados](./creating-custom-controls.md)

[Definir conjuntos de selección](./defining-selection-sets.md)

[Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

[Elemento TypeName (formato)](./typename-element-for-viewselectedby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
