---
title: Crear una vista amplia | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368954"
---
# <a name="creating-a-wide-view"></a>Creación de una vista amplia

Una vista amplia muestra un valor único para cada objeto que se muestra. El valor mostrado puede ser el valor de una propiedad de objeto .NET o el valor de un script. De forma predeterminada, no hay ninguna etiqueta o encabezado para esta vista.

## <a name="a-wide-view-display"></a>Visualización de vista amplia

En el ejemplo siguiente se muestra cómo Windows PowerShell muestra el objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) que devuelve el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cuando su salida se canaliza al cmdlet [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) . (De forma predeterminada, el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) devuelve una vista de tabla). En este ejemplo, se usan las dos columnas para mostrar el nombre del proceso para cada objeto devuelto. No se muestra el nombre de la propiedad del objeto, solo el valor de la propiedad.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Definir la vista amplia

El XML siguiente muestra el esquema de vista ancha para el objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Los siguientes elementos XML se utilizan para definir una vista ampliada:

- El elemento de [vista](./view-element-format.md) es el elemento primario de la vista amplia. (Este es el mismo elemento primario para las vistas de tabla, lista y control personalizado).

- El elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista. Este elemento es necesario para todas las vistas.

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista. Se requiere el elemento.

- El elemento [GroupBy](./groupby-element-for-view-format.md) define cuándo se muestra un nuevo grupo de objetos. Se inicia un nuevo grupo siempre que cambia el valor de una propiedad o un script específicos. Este elemento es opcional.

- Los elementos [Controls](./controls-element-for-view-format.md) definen los controles personalizados que se definen en la vista amplia. Los controles ofrecen una manera de especificar mejor cómo se muestran los datos. Este elemento es opcional. Una vista puede definir sus propios controles personalizados o puede usar controles comunes que se pueden usar en cualquier vista del archivo de formato. Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).

- El elemento [WideControl](./widecontrol-element-format.md) y sus elementos secundarios definen lo que se muestra en la vista. En el ejemplo anterior, la vista está diseñada para mostrar la propiedad [System. Diagnostics. Process. processName](/dotnet/api/System.Diagnostics.Process.ProcessName) .

Para obtener un ejemplo de un archivo de formato completo que define una vista ancha sencilla, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Proporcionar definiciones para la vista amplia

Las vistas anchas pueden proporcionar una o más definiciones mediante el uso de los elementos secundarios del elemento [WideControl](./widecontrol-element-format.md) . Normalmente, una vista solo tendrá una definición. En el ejemplo siguiente, la vista proporciona una única definición que muestra el valor de la propiedad [System. Diagnostics. Process. processName](/dotnet/api/System.Diagnostics.Process.ProcessName) . Una vista amplia puede mostrar el valor de una propiedad o el valor de un script (no se muestra en el ejemplo).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Los siguientes elementos XML se pueden usar para proporcionar definiciones para una vista amplia:

- El elemento [WideControl](./widecontrol-element-format.md) y sus elementos secundarios definen lo que se muestra en la vista.

- El elemento [AutoSize](./autosize-element-for-widecontrol-format.md) especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos. Este elemento es opcional.

- El elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) especifica el número de columnas que se muestran en la vista amplia. Este elemento es opcional.

- El elemento [WideEntries](./wideentries-element-for-widecontrol-format.md) proporciona las definiciones de la vista. En la mayoría de los casos, una vista solo tendrá una definición. Se requiere el elemento.

- El elemento [WideEntry](./wideentry-element-for-widecontrol-format.md) proporciona una definición de la vista. Se requiere al menos un [WideEntry](./wideentry-element-for-widecontrol-format.md) ; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar. En la mayoría de los casos, una vista solo tendrá una definición.

- El elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) especifica los objetos que se muestran en una definición específica. Este elemento es opcional y solo es necesario cuando se definen varios elementos [WideEntry](./wideentry-element-for-widecontrol-format.md) que muestran objetos diferentes.

- El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) especifica los datos que se muestran en la vista. A diferencia de otros tipos de vistas, un control ancho solo puede mostrar un elemento.

- El elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) especifica la propiedad cuyo valor se muestra en la vista. Debe especificar una propiedad o un script, pero no puede especificar ambos.

- El elemento [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) especifica el script cuyo valor se muestra en la vista. Debe especificar un script o una propiedad, pero no puede especificar ambos.

- El elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) especifica un patrón que se usa para mostrar los datos. Este elemento es opcional.

Para obtener un ejemplo de un archivo de formato completo que define una definición de vista ancha, vea [vista ampliada (básica)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definir los objetos que usan la vista amplia

Hay dos maneras de definir qué objetos .NET usan la vista amplia. Puede usar el elemento [ViewSelectedBy](./viewselectedby-element-format.md) para definir los objetos que se pueden mostrar en todas las definiciones de la vista, o puede usar el elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) para definir qué objetos se muestran en una definición específica de la vista. En la mayoría de los casos, una vista solo tiene una definición, por lo que los objetos se definen normalmente mediante el elemento [ViewSelectedBy](./viewselectedby-element-format.md) .

En el ejemplo siguiente se muestra cómo definir los objetos que se muestran en la vista amplia mediante los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) . No hay ningún límite en el número de elementos [TypeName](./typename-element-for-viewselectedby-format.md) que se pueden especificar y su orden no es significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista ampliada:

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista amplia.

- El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el .net que se muestra en la vista. El nombre completo del tipo .NET es obligatorio. Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

Para obtener un ejemplo de un archivo de formato completo, vea [vista ampliada (básica)](./wide-view-basic.md).

En el ejemplo siguiente se usan los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Use conjuntos de selección en los que tenga un conjunto relacionado de objetos que se muestran mediante varias vistas, como cuando se define una vista amplia y una vista de tabla para los mismos objetos. Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista ampliada:

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista amplia.

- El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos que se pueden mostrar en la vista. Debe especificar al menos un conjunto o tipo de selección para la vista, pero no se puede especificar un número máximo de elementos.

En el ejemplo siguiente se muestra cómo definir los objetos mostrados por una definición específica de la vista ampliada mediante el elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) . Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que especifica cuándo se usa la definición. Para obtener más información sobre cómo crear condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en una definición específica de la vista ampliada:

- El elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) define qué objetos se muestran en la definición.

- El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el .net que se muestra en la definición. Cuando se usa este elemento, se requiere el nombre de tipo .NET completo. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (no se muestra) especifica un conjunto de objetos que se pueden mostrar en esta definición. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (no se muestra) especifica una condición que debe existir para que se use esta definición. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar. Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Mostrar grupos de objetos en una vista amplia

Puede separar los objetos que se muestran en la vista amplia en grupos. Esto no significa que defina un grupo, solo que Windows PowerShell inicie un nuevo grupo siempre que cambie el valor de una propiedad o un script específicos. En el ejemplo siguiente, se inicia un nuevo grupo siempre que cambia el valor de la propiedad [System. ServiceProcess. ServiceController. serviceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Los siguientes elementos XML se utilizan para definir cuándo se inicia un grupo:

- El elemento [GroupBy](./groupby-element-for-view-format.md) define la propiedad o el script que inicia el nuevo grupo y define cómo se muestra el grupo.

- El elemento [PropertyName](./propertyname-element-for-groupby-format.md) especifica la propiedad que inicia un nuevo grupo cada vez que cambia su valor. Debe especificar una propiedad o un script para iniciar el grupo, pero no puede especificar ambos.

- El elemento [ScriptBlock](./scriptblock-element-for-groupby-format.md) especifica el script que inicia un nuevo grupo cada vez que cambia su valor. Debe especificar un script o una propiedad para iniciar el grupo, pero no puede especificar ambos.

- El elemento [Label](./label-element-for-groupby-format.md) define una etiqueta que se muestra al principio de cada grupo. Además del texto especificado por este elemento, Windows PowerShell muestra el valor que desencadenó el nuevo grupo y agrega una línea en blanco antes y después de la etiqueta. Este elemento es opcional.

- El elemento [CustomControl](./customcontrol-element-for-groupby-format.md) define un control que se utiliza para mostrar los datos. Este elemento es opcional.

- El elemento [CustomControlName](./customcontrolname-element-for-groupby-format.md) especifica un control común o de vista que se usa para mostrar los datos. Este elemento es opcional.

Para obtener un ejemplo de un archivo de formato completo que define grupos, vea [vista ampliada (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Usar cadenas de formato

Las cadenas de formato se pueden agregar a una vista amplia para definir mejor cómo se muestran los datos. En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Los siguientes elementos XML se pueden usar para especificar un modelo de formato:

- El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) especifica los datos que se muestran en la vista.

- El elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) especifica la propiedad cuyo valor se muestra en la vista. Debe especificar una propiedad o un script, pero no puede especificar ambos.

- El elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.

- El elemento [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista. Debe especificar un script o una propiedad, pero no puede especificar ambos.

En el ejemplo siguiente, se llama al método `ToString` para dar formato al valor del script. Los scripts pueden llamar a cualquier método de un objeto. Por consiguiente, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida del script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

El siguiente elemento XML se puede usar para llamar al método `ToString`:

- El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) especifica los datos que se muestran en la vista.

- El elemento [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista. Debe especificar un script o una propiedad, pero no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Vista amplia (básica)](./wide-view-basic.md)

[Vista amplia (GroupBy)](./wide-view-groupby.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
