---
title: Elemento View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361464"
---
# <a name="view-element-format"></a>Elemento View (formato)

Define una vista que muestra uno o más objetos .NET. No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format)

## <a name="syntax"></a>Sintaxis

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `View`. Debe especificar uno y solo uno de los elementos secundarios de control, y debe especificar el nombre de la vista y los objetos que la usan. Definir controles personalizados, agrupar objetos y especificar si la vista está fuera de banda es opcional.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Controls (elemento) para View (Format)](./controls-element-for-view-format.md)|Elemento opcional.<br /><br /> Define un conjunto de controles a los que se puede hacer referencia mediante su nombre desde dentro de la vista.|
|[CustomControl (elemento, Format)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define un formato de control personalizado para la vista.|
|[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)|Elemento opcional.<br /><br /> Define cómo se agrupan los miembros de los objetos .NET.|
|[ListControl (elemento, Format)](./listcontrol-element-format.md)|Elemento opcional.<br /><br /> Define un formato de lista para la vista.|
|[Name (elemento) para View (Format)](./name-element-for-view-format.md)|Elemento necesario.<br /><br /> Especifica el nombre usado para hacer referencia a la vista.|
|[Elemento Tablecontrol ((Format)](./tablecontrol-element-format.md)|Elemento opcional.<br /><br /> Define un formato de tabla para la vista.|
|[Elemento ViewSelectedBy para View (Format)](./viewselectedby-element-format.md)|Elemento necesario.<br /><br /> Define los objetos .NET que muestra esta vista.|
|[Elemento WideControl (Format)](./widecontrol-element-format.md)|Elemento opcional.<br /><br /> Define un formato de lista ancho (valor único) para la vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Define las vistas que se usan para mostrar los objetos.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de diferentes vistas y controles personalizados, vea los temas siguientes:

- [Componentes de vista de tabla](./creating-a-table-view.md)

- [Componentes de la vista de lista](./creating-a-list-view.md)

- [Componentes de vista ancha](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `View` que define una vista de tabla para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Véase también

[Elemento ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Name (elemento) para View (Format)](./name-element-for-view-format.md)

[Elemento ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Controls (elemento) para View (Format)](./controls-element-for-view-format.md)

[Elemento GroupBy para View (Format)](./groupby-element-for-view-format.md)

[Elemento Tablecontrol ((Format)](./tablecontrol-element-format.md)

[ListControl (elemento, Format)](./listcontrol-element-format.md)

[Elemento WideControl (Format)](./widecontrol-element-format.md)

[CustomControl (elemento, Format)](./customcontrol-element-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
