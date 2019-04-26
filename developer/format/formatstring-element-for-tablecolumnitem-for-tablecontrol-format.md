---
title: Elemento FormatString para TableColumnItem para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065644"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>Elemento FormatString para TableColumnItem for TableControl (formato)

Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script de la tabla.

Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento de configuración (formato) Elemento FormatString para TableColumnItem (formato)

## <a name="syntax"></a>Sintaxis

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `FormatString` elemento.

### <a name="attributes"></a>Atributos

Ninguna.

### <a name="child-elements"></a>Elementos secundarios

Ninguna.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Define la propiedad o el script cuyo valor se muestra en la columna de la fila.|

## <a name="text-value"></a>Valor de texto

Especifique el patrón que se usa para dar formato a los datos. Por ejemplo, este patrón se puede usar para dar formato al valor de cualquier propiedad que es del tipo [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Observaciones

Cadenas de formato pueden usarse al crear las vistas de tablas, vistas de lista, vista amplia o vistas personalizadas. Para obtener más información sobre cómo dar formato a un valor que se muestran en una vista, consulte [dar formato a datos de muestra](./formatting-displayed-data.md).

Para obtener más información acerca de los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Véase también

[Creación de una vista de tabla](./creating-a-table-view.md)

[Aplicar formato a los datos mostrados](./formatting-displayed-data.md)

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
