---
title: Crear una vista de tabla | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363414"
---
# <a name="creating-a-table-view"></a>Creación de una vista de tabla

Una vista de tabla muestra los datos en una o varias columnas. Cada fila de la tabla representa un objeto .NET y cada columna de la tabla representa una propiedad del objeto o un valor de script. Puede definir una vista de tabla que muestre todas las propiedades de un objeto o un subconjunto de las propiedades de un objeto.

## <a name="a-table-view-display"></a>Visualización de una vista de tabla

En el ejemplo siguiente se muestra cómo Windows PowerShell muestra el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) devuelto por el cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) . Para este objeto, Windows PowerShell ha definido una vista de tabla que muestra la propiedad `Status`, la propiedad `Name` (esta propiedad es una propiedad de alias para la propiedad `ServiceName`) y la propiedad `DisplayName`. Cada fila de la tabla representa un objeto devuelto por el cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definir la vista de tabla

El siguiente XML muestra el esquema de la vista de tabla para mostrar [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) (objeto). Debe especificar cada propiedad que desea que se muestre en la vista de tabla.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Los siguientes elementos XML se utilizan para definir una vista de lista:

- El elemento de [vista](./view-element-format.md) es el elemento primario de la vista de tabla. (Es el mismo elemento primario para las vistas de lista, ancho y control personalizado).

- El elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista. Este elemento es necesario para todas las vistas.

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista. Este elemento es obligatorio.

- El elemento [GroupBy](./groupby-element-for-view-format.md) (no se muestra en este ejemplo) define cuándo se muestra un nuevo grupo de objetos. Se inicia un nuevo grupo siempre que cambia el valor de una propiedad o un script específicos. Este elemento es opcional.

- El elemento [Controls](./controls-element-for-view-format.md) (no se muestra en este ejemplo) define los controles personalizados que se definen en la vista de tabla. Los controles ofrecen una manera de especificar mejor cómo se muestran los datos. Este elemento es opcional. Una vista puede definir sus propios controles personalizados o puede usar controles comunes que se pueden usar en cualquier vista del archivo de formato. Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).

- El elemento [HideTableHeaders](./hidetableheaders-element-format.md) (no se muestra en este ejemplo) especifica que la tabla no mostrará ninguna etiqueta en la parte superior de la tabla. Este elemento es opcional.

- El elemento [tablecontrol (](./tablecontrol-element-format.md) que define la información de encabezado y fila de la tabla. Al igual que todas las demás vistas, una vista de tabla puede mostrar los valores de las propiedades de objeto o de los valores generados por scripts.

## <a name="defining-column-headers"></a>Definir encabezados de columna

1. El elemento [TableHeaders](./tableheaders-element-format.md) y sus elementos secundarios definen lo que se muestra en la parte superior de la tabla.

2. El elemento [TableColumnHeader](./tablecolumnheader-element-format.md) define lo que se muestra en la parte superior de una columna de la tabla. Especifique estos elementos en el orden en que desea que se muestren los encabezados.

   No hay ningún límite en cuanto al número de estos elementos que puede utilizar, pero el número de elementos [TableColumnHeader](./tablecolumnheader-element-format.md) en la vista de tabla debe ser igual al número de elementos [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) que use.

3. El elemento [etiqueta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) especifica el texto que se muestra. Este elemento es opcional.

4. El elemento [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) especifica el ancho (en caracteres) de la columna. Este elemento es opcional.

5. El elemento [alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) especifica cómo se muestra la etiqueta. La etiqueta se puede alinear a la izquierda, a la derecha o centrada. Este elemento es opcional.

## <a name="defining-the-table-rows"></a>Definir las filas de la tabla

Las vistas de tabla pueden proporcionar una o más definiciones que especifican qué datos se muestran en las filas de la tabla mediante los elementos secundarios del elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) . Tenga en cuenta que puede especificar varias definiciones para las filas de la tabla, pero los encabezados de las filas siguen siendo los mismos, independientemente de la definición de fila que se utilice. Normalmente, una tabla solo tendrá una definición.

En el ejemplo siguiente, la vista proporciona una única definición que muestra los valores de varias propiedades de [System. Diagnostics. Process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) (objeto). Una vista de tabla puede mostrar el valor de una propiedad o el valor de un script (no se muestra en el ejemplo) en sus filas.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Los siguientes elementos XML se pueden usar para proporcionar definiciones para una fila:

- El elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) y sus elementos secundarios definen lo que se muestra en las filas de la tabla.

- El elemento [TableRowEntry](./listentry-element-for-listcontrol-format.md) proporciona una definición de la fila. Se requiere al menos un [TableRowEntry](./listentry-element-for-listcontrol-format.md) ; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar. En la mayoría de los casos, una vista solo tendrá una definición.

- El elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) especifica los objetos que se muestran en una definición específica. Este elemento es opcional y solo es necesario cuando se definen varios elementos [TableRowEntry](./listentry-element-for-listcontrol-format.md) que muestran objetos diferentes.

- El elemento [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) especifica que el texto que supera el ancho de columna se muestra en la línea siguiente. De forma predeterminada, el texto que supera el ancho de columna se trunca.

- El elemento [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) define las propiedades o los scripts cuyos valores se muestran en la fila.

- El elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila. Se requiere un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.

- El elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica la propiedad cuyo valor se muestra en la fila. Debe especificar una propiedad o un script, pero no puede especificar ambos.

- El elemento [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica el script cuyo valor se muestra en la fila. Debe especificar un script o una propiedad, pero no puede especificar ambos.

- El elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script. Este elemento es opcional.

- El elemento [alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica cómo se muestra el valor de la propiedad o el script. El valor se puede alinear a la izquierda, a la derecha o al centro. Este elemento es opcional.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definir los objetos que utilizan la vista de tabla

Hay dos maneras de definir qué objetos .NET usan la vista de tabla. Puede usar el elemento [ViewSelectedBy](./viewselectedby-element-format.md) para definir los objetos que se pueden mostrar en todas las definiciones de la vista, o puede usar el elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) para definir qué objetos se muestran en una definición específica de la vista. En la mayoría de los casos, una vista solo tiene una definición, por lo que los objetos se definen normalmente mediante el elemento [ViewSelectedBy](./viewselectedby-element-format.md) .

En el ejemplo siguiente se muestra cómo definir los objetos que se muestran en la vista de tabla mediante los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) . No hay ningún límite en el número de elementos [TypeName](./typename-element-for-viewselectedby-format.md) que se pueden especificar y su orden no es significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Los siguientes elementos XML se pueden utilizar para especificar los objetos que se usan en la vista de tabla:

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.

- El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el objeto .net que se muestra en la vista. El nombre completo del tipo .NET es obligatorio. Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

En el ejemplo siguiente se usan los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Use conjuntos de selección en los que tenga un conjunto relacionado de objetos que se muestran mediante varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos. Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista de lista:

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.

- El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos que se pueden mostrar en la vista. Debe especificar al menos un conjunto o tipo de selección para la vista, pero no se puede especificar un número máximo de elementos.

En el ejemplo siguiente se muestra cómo definir los objetos mostrados por una definición específica de la vista de tabla mediante el elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) . Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que especifica cuándo se usa la definición. Para obtener más información sobre cómo crear condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Al crear varias definiciones de la vista de tabla, no puede especificar encabezados de columna diferentes. Solo puede especificar lo que se muestra en las filas de la tabla, como los objetos que se muestran.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en una definición específica de la vista de lista:

- El elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) define qué objetos se muestran en la definición.

- El elemento [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) especifica el objeto .net que se muestra en la definición. Al usar este elemento, se requiere el nombre completo del tipo .NET. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica un conjunto de objetos que se pueden mostrar en esta definición. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica una condición que debe existir para que se use esta definición. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar. Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Usar cadenas de formato

Las cadenas de formato se pueden agregar a una vista para definir mejor cómo se muestran los datos. En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Los siguientes elementos XML se pueden usar para especificar un modelo de formato:

- El elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila. Se requiere un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.

- El elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica la propiedad cuyo valor se muestra en la fila. Debe especificar una propiedad o un script, pero no puede especificar ambos.

- El elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script.

En el ejemplo siguiente, se llama al método `ToString` para dar formato al valor del script. Los scripts pueden llamar a cualquier método de un objeto. Por consiguiente, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida del script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

El siguiente elemento XML se puede usar para llamar al método `ToString`:

- El elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila. Se requiere un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.

- El elemento [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica el script cuyo valor se muestra en la fila. Debe especificar un script o una propiedad, pero no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
