---
title: Elemento TableColumnItem para TableColumnItems para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368234"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Elemento TableColumnItem para TableColumnItems for TableControl (formato)

Define la propiedad o el script cuyo valor se muestra en la columna de la fila.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries para Tablecontrol ((Format) elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format) Elemento TableColumnItems para TableControlEntry para Tablecontrol ((Format) elemento TableColumnItem para TableColumnItems para Tablecontrol ((Format)

## <a name="syntax"></a>Sintaxis

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableColumnItem`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Alignment para TableColumnItem para Tablecontrol ((Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define cómo se muestran los datos de una columna de la fila.|
|[Elemento FormatString para TableColumnItem para Tablecontrol ((Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Especifica un modelo de formato que se utiliza para dar formato a los datos de la columna de la fila.|
|[Elemento PropertyName para TableColumnItem para Tablecontrol ((Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el nombre de la propiedad cuyo valor se muestra.|
|[Elemento ScriptBlock para TableColumnItem para Tablecontrol ((Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica el script cuyo valor se muestra en la columna de una fila.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItems para TableControlEntry para Tablecontrol ((Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Define las propiedades o los scripts cuyos valores se muestran en la fila.|

## <a name="remarks"></a>Observaciones

Puede especificar una propiedad de un objeto o un script en cada columna de la fila. Si no se especifica ningún elemento secundario, el elemento es un marcador de posición y no se muestra ningún dato.

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `TableColumnItem` que muestra el valor de la propiedad `Status` del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento Alignment para TableColumnItem para Tablecontrol ((Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento TableColumnItems (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento FormatString para TableColumnItem para Tablecontrol ((Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento PropertyName para TableColumnItem para Tablecontrol ((Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento ScriptBlock para TableColumnItem para Tablecontrol ((Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
