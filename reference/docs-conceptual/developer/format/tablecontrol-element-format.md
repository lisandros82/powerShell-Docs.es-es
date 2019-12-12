---
title: Elemento Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368204"
---
# <a name="tablecontrol-element-format"></a>Elemento TableControl (formato)

Define un formato de tabla para una vista.

Elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format)

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

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableControl`. Debe especificar las filas de la tabla. Todos los demás elementos secundarios son opcionales.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[AutoSize (elemento) para Tablecontrol ((Format)](./autosize-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.|
|[Elemento HideTableHeaders para Tablecontrol ((Format)](./hidetableheaders-element-format.md)|Elemento opcional.<br /><br /> Indica si no se muestra el encabezado de la tabla.|
|[Elemento TableHeaders para Tablecontrol ((Format)](./tableheaders-element-format.md)|Elemento necesario.<br /><br /> Define las etiquetas, el ancho y la alineación de los datos para las columnas de la vista de tabla.|
|[Elemento TableRowEntries para Tablecontrol ((Format)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Proporciona las definiciones de la vista de tabla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento View (Format)](./view-element-format.md)|Define una vista que se utiliza para mostrar los miembros de uno o más objetos.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `TableControl` que se utiliza para mostrar las propiedades del objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento View (Format)](./view-element-format.md)

[AutoSize (elemento) para Tablecontrol ((Format)](./autosize-element-for-tablecontrol-format.md)

[Elemento HideTableHeaders (Format)](./hidetableheaders-element-format.md)

[Elemento TableHeaders (Format)](./tableheaders-element-format.md)

[Elemento TableRowEntries (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
