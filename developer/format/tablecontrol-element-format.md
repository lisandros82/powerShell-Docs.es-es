---
title: Elemento TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858921"
---
# <a name="tablecontrol-element-format"></a>Elemento TableControl (formato)

Define un formato de tabla para obtener una vista.

Elemento ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato)

## <a name="syntax"></a>Sintaxis

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableControl` elemento. Debe especificar las filas de la tabla. Todos los demás elementos secundarios son opcionales.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento AutoSize para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.|
|[Elemento HideTableHeaders para TableControl (formato)](./hidetableheaders-element-format.md)|Elemento opcional.<br /><br /> Indica si el encabezado de la tabla no se muestra.|
|[Elemento TableHeaders para TableControl (formato)](./tableheaders-element-format.md)|Elemento necesario.<br /><br /> Define las etiquetas, el ancho y la alineación de los datos para las columnas de la vista de tabla.|
|[Elemento TableRowEntries para TableCotrol (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Proporciona las definiciones de la vista de tabla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento de vista (formato)](./view-element-format.md)|Define una vista que se usa para mostrar a los miembros de uno o varios objetos.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `TableControl` elemento que se utiliza para mostrar las propiedades de la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento de vista (formato)](./view-element-format.md)

[Elemento AutoSize para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)

[Elemento HideTableHeaders (formato)](./hidetableheaders-element-format.md)

[Elemento TableHeaders (formato)](./tableheaders-element-format.md)

[Elemento TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
