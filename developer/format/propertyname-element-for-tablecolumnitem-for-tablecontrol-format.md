---
title: Elemento PropertyName para TableColumnItem para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064620"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento PropertyName para TableColumnItem for TableControl (formato)

Especifica la propiedad cuyo valor se muestra en la columna de la fila.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento de configuración (formato) Elemento PropertyName para TableColumnItem (formato)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en la columna de la fila.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un `TableColumnItem` elemento que especifica el `Status` propiedad de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
