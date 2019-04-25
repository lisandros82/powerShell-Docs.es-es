---
title: Creación de una vista de tabla | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066845"
---
# <a name="creating-a-table-view"></a>Creación de una vista de tabla

Una vista de tabla muestra los datos en una o varias columnas. Cada fila de la tabla representa un objeto. NET, y cada columna de la tabla representa una propiedad del objeto o un valor de la secuencia de comandos. Puede definir una vista de tabla que muestra todas las propiedades de un objeto o un subconjunto de las propiedades de un objeto.

## <a name="a-table-view-display"></a>Una presentación de la vista de tabla

El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Para este objeto, Windows PowerShell ha definido una vista de tabla que muestra la `Status` propiedad, el `Name` propiedad (esta propiedad es una propiedad de alias para el `ServiceName` propiedad) y el `DisplayName` propiedad. Cada fila de la tabla representa un objeto devuelto por el cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Define la vista de tabla

¿El siguiente XML muestra el esquema de vista de tabla para mostrar el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto. Debe especificar cada propiedad que desea que aparezca en la vista de tabla.

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

Los siguientes elementos XML se usan para definir una vista de lista:

- El [vista](./view-element-format.md) elemento es el elemento primario de la vista de tabla. (Esto es el mismo elemento primario de la lista, las vistas de control ancho y personalizadas).

- El [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista. Este elemento es necesario para todas las vistas.

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista. Este elemento es necesario.

- El [GroupBy](./groupby-element-for-view-format.md) elemento (no se muestra en este ejemplo) define cuando se muestre un nuevo grupo de objetos. Cada vez que cambia el valor de una propiedad específica o un script, se inicia un nuevo grupo. Este elemento es opcional.

- El [controles](./controls-element-for-view-format.md) elemento (no se muestra en este ejemplo) define los controles personalizados que se definen mediante la vista de tabla. Los controles ofrecen una manera de especificar cómo se muestran los datos. Este elemento es opcional. Una vista puede definir sus propios controles personalizados, o puede usar controles comunes que pueden usarse en cualquier vista en el archivo de formato. Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).

- El [HideTableHeaders](./hidetableheaders-element-format.md) elemento (no aparece en este ejemplo) especifica que la tabla no mostrará ninguna etiqueta en la parte superior de la tabla. Este elemento es opcional.

- El [TableControl](./tablecontrol-element-format.md) elemento que define la información de encabezado y fila de la tabla. Al igual que todas las demás vistas, una vista de tabla puede mostrar los valores de las propiedades del objeto o los valores generados por las secuencias de comandos.

## <a name="defining-column-headers"></a>Definir los encabezados de columna

1. El [TableHeaders](./tableheaders-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la parte superior de la tabla.

2. El [TableColumnHeader](./tablecolumnheader-element-format.md) elemento define lo que se muestra en la parte superior de una columna de la tabla. Estos elementos se especifican en el orden en que desea que los encabezados se muestran.

   No hay ningún límite en el número de estos elementos que puede usar, pero el número de [TableColumnHeader](./tablecolumnheader-element-format.md) elementos en la vista de tabla deben ser igual al número de [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementos que se usan.

3. El [etiqueta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento especifica el texto que se muestra. Este elemento es opcional.

4. El [ancho](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento especifica el ancho (en caracteres) de la columna. Este elemento es opcional.

5. El [alineación](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento especifica cómo se muestra la etiqueta. La etiqueta se alinea a la izquierda, a la derecha, o centrada. Este elemento es opcional.

## <a name="defining-the-table-rows"></a>Definir las filas de tabla

Vistas de tabla pueden proporcionar una o varias definiciones que especifican qué datos se muestran en las filas de la tabla mediante el uso de los elementos secundarios de la [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento. Tenga en cuenta que puede especificar varias definiciones para las filas de la tabla, pero los encabezados de las filas sigue siendo el mismo, independientemente de qué definición de fila se utiliza. Por lo general, una tabla tiene una única definición.

¿En el ejemplo siguiente, la vista proporciona una única definición que muestra los valores de varias propiedades de la [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto. Una vista de tabla puede mostrar el valor de una propiedad o el valor de una secuencia de comandos (no se muestra en el ejemplo) en sus filas.

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

Los siguientes elementos XML pueden usarse para proporcionar las definiciones para una fila:

- El [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento y sus elementos secundarios definen lo que se muestra en las filas de la tabla.

- El [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento proporciona una definición de la fila. Al menos un [TableRowEntry](./listentry-element-for-listcontrol-format.md) es necesario; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar. En la mayoría de los casos, una vista tendrá una única definición.

- El [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento especifica los objetos que se muestran en una definición específica. Este elemento es opcional y solo es necesario cuando definir varios [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementos que muestran los distintos objetos.

- El [ajustar](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elemento especifica que el texto que supera el ancho de columna se muestra en la línea siguiente. De forma predeterminada, el texto que supera el ancho de columna se trunca.

- El [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento define las propiedades o scripts cuyos valores se muestran en la fila.

- El [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define la propiedad o el script cuyo valor se muestra en la columna de la fila. Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento es necesario para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.

- El [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra en la fila. Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.

- El [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra en la fila. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

- El [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script. Este elemento es opcional.

- El [alineación](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica cómo se muestra el valor de la propiedad o el script. El valor puede ser alineado a la izquierda, a la derecha, o centrado. Este elemento es opcional.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definir los objetos que utilizan la vista de tabla

Hay dos maneras de definir qué objetos de .NET utilizan la vista de tabla. Puede usar el [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir los objetos que se pueden mostrar todas las definiciones de la vista, o bien puede usar el [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir qué objetos se muestran mediante un definición específica de la vista. En la mayoría de los casos, una vista tiene una única definición, por lo que normalmente se definen los objetos mediante el [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

El ejemplo siguiente muestra cómo se definen los objetos que se muestran en la vista de tabla mediante el [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) elementos. No hay ningún límite al número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que puede especificar y su orden no es significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de tabla:

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.

- El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica el objeto .NET que se muestra la vista. Se requiere el nombre de tipo .NET completo. Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

En el ejemplo siguiente se usa el [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Usar conjuntos de selección donde haya un conjunto de objetos que se muestran usando varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos relacionados. Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de lista:

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.

- El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento especifica un conjunto de objetos que se puede mostrar la vista. Debe especificar al menos un conjunto de selección o tipo de la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

El ejemplo siguiente muestra cómo definir los objetos mostrados por una definición específica de la vista de tabla mediante el [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento. Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que se especifica cuando se usa la definición. Para obtener más información acerca de cómo crear una selección de las condiciones, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Al crear varias definiciones de la vista de tabla no se puede especificar encabezados de columna diferente. Puede especificar sólo lo que se muestra en las filas de la tabla, como los objetos que se muestran.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Los siguientes elementos XML pueden usarse para especificar los objetos usados por una definición específica de la vista de lista:

- El [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento define los objetos que se muestran en la definición.

- El [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento especifica el objeto .NET que se muestra la definición. Cuando se usa este elemento, se requiere el nombre de tipo .NET completo. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica un conjunto de objetos que se pueden mostrar por esta definición. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica una condición que debe existir para que esta definición para usarse. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar. Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Usar cadenas de formato

Las cadenas de formato se pueden agregar a una vista para definir cómo se muestran los datos. El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Los siguientes elementos XML pueden usarse para especificar un patrón de formato:

- El [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define la propiedad o el script cuyo valor se muestra en la columna de la fila. Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento es necesario para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.

- El [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra en la fila. Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.

- El [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script.

En el ejemplo siguiente, la `ToString` método se llama para dar formato al valor de la secuencia de comandos. Las secuencias de comandos pueden llamar a cualquier método de un objeto. Por lo tanto, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida de la secuencia de comandos.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

El siguiente elemento XML puede usarse para llamar a la `ToString` método:

- El [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define la propiedad o el script cuyo valor se muestra en la columna de la fila. Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento es necesario para cada columna de la fila. La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.

- El [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra en la fila. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

## <a name="see-also"></a>Véase también

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
