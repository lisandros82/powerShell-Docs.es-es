---
title: Ver elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083729"
---
# <a name="view-element-format"></a>Elemento View (formato)

Define una vista que muestra uno o varios objetos. NET. No hay ningún límite al número de vistas que se pueden definir en un archivo de formato.

Elemento de vista de configuración (formato) del elemento elemento ViewDefinitions (formato) (formato)

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

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `View` elemento. Debe especificar solo uno de los elementos secundarios de control, y debe especificar el nombre de la vista y los objetos que utilizan la vista. Definir controles personalizados, cómo agrupar objetos, y especifica si la vista está fuera de banda son opcionales.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Los controles elemento de vista (formato)](./controls-element-for-view-format.md)|Elemento opcional.<br /><br /> Define un conjunto de controles que pueden hacer referencia por su nombre desde dentro de la vista.|
|[Elemento de control personalizado (formato)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define un formato de control personalizado para la vista.|
|[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)|Elemento opcional.<br /><br /> Define cómo se agrupan los miembros de los objetos. NET.|
|[Elemento ListControl (formato)](./listcontrol-element-format.md)|Elemento opcional.<br /><br /> Define un formato de lista para la vista.|
|[Elemento Name de vista (formato)](./name-element-for-view-format.md)|Elemento necesario.<br /><br /> Especifica el nombre usado para hacer referencia a la vista.|
|[Elemento TableControl (formato)](./tablecontrol-element-format.md)|Elemento opcional.<br /><br /> Define un formato de tabla para la vista.|
|[Elemento ViewSelectedBy para vista (formato)](./viewselectedby-element-format.md)|Elemento necesario.<br /><br /> Define los objetos de .NET que muestra esta vista.|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Elemento opcional.<br /><br /> Define una amplia (valor single) formato de lista para la vista.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Define las vistas que se usa para mostrar los objetos.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de diferentes vistas y los controles personalizados, vea los temas siguientes:

- [Componentes de vista de tabla](./creating-a-table-view.md)

- [Componentes de vista de lista](./creating-a-list-view.md)

- [Componentes de vista ampliada](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `View` elemento que define una vista de tabla para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

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

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Elemento Name de vista (formato)](./name-element-for-view-format.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Los controles elemento de vista (formato)](./controls-element-for-view-format.md)

[Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)

[Elemento TableControl (formato)](./tablecontrol-element-format.md)

[Elemento ListControl (formato)](./listcontrol-element-format.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Elemento de control personalizado (formato)](./customcontrol-element-for-groupby-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
