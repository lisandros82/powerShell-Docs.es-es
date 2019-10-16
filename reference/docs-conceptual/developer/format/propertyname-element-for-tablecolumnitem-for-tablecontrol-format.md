---
title: Elemento PropertyName para TableColumnItem para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362254"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento PropertyName para TableColumnItem for TableControl (formato)

Especifica la propiedad cuyo valor se muestra en la columna de la fila.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento PropertyName para TableColumnItem (Format)

## <a name="syntax"></a>Sintaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en la columna de la fila.|

## <a name="text-value"></a>Valor de texto

Especifique el nombre de la propiedad cuyo valor se muestra.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un elemento `TableColumnItem` que especifica la propiedad `Status` del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
