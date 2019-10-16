---
title: Elemento FormatString para TableColumnItem para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363714"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento FormatString para TableColumnItem for TableControl (formato)

Especifica un modelo de formato que define cómo se muestra el valor de la propiedad o el script de la tabla.

Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento FormatString para TableColumnItem (Format)

## <a name="syntax"></a>Sintaxis

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FormatString`.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en la columna de la fila.|

## <a name="text-value"></a>Valor de texto

Especifique el patrón que se utiliza para dar formato a los datos. Por ejemplo, este patrón se puede usar para dar formato al valor de cualquier propiedad que sea del tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: HH}: {0: mm}.

## <a name="remarks"></a>Observaciones

Las cadenas de formato se pueden usar al crear vistas de tabla, vistas de lista, vistas anchas o vistas personalizadas. Para obtener más información sobre cómo dar formato a un valor que se muestra en una vista, vea [aplicar formato a los datos mostrados](./formatting-displayed-data.md).

Para obtener más información sobre los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Véase también

[Crear una vista de tabla](./creating-a-table-view.md)

[Aplicar formato a los datos mostrados](./formatting-displayed-data.md)

[Elemento TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
