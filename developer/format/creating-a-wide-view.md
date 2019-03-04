---
title: Creación de una vista amplia | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858501"
---
# <a name="creating-a-wide-view"></a>Creación de una vista amplia

Una vista amplia muestra un valor único para cada objeto que se muestra. El valor de una propiedad de objeto .NET o el valor de una secuencia de comandos, puede ser el valor mostrado. De forma predeterminada, no hay ninguna etiqueta ni el encabezado para esta vista.

## <a name="a-wide-view-display"></a>Una presentación de la vista ampliada

El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto devuelto por la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet cuando su salida se canaliza hacia el [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (De forma predeterminada, el [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devuelve una vista de tabla.) En este ejemplo, las dos columnas se utilizan para mostrar el nombre del proceso para cada objeto devuelto. No se muestra el nombre de la propiedad del objeto, solo el valor de la propiedad.

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

## <a name="defining-the-wide-view"></a>Define la vista ancha

El siguiente XML muestra el esquema de la vista ampliada para la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.

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

Los siguientes elementos XML se usan para definir una vista amplia:

- El [vista](./view-element-format.md) elemento es el elemento primario de la vista ampliada. (Esto es el mismo elemento primario para la tabla, lista y vistas de control personalizado).

- El [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista. Este elemento es necesario para todas las vistas.

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista. Este elemento es necesario.

- El [GroupBy](./groupby-element-for-view-format.md) elemento define cuando se muestre un nuevo grupo de objetos. Cada vez que cambia el valor de una propiedad específica o un script, se inicia un nuevo grupo. Este elemento es opcional.

- El [controles](./controls-element-for-view-format.md) elementos define los controles personalizados que se definen mediante la vista ampliada. Los controles ofrecen una manera de especificar cómo se muestran los datos. Este elemento es opcional. Una vista puede definir sus propios controles personalizados, o puede usar controles comunes que pueden usarse en cualquier vista en el archivo de formato. Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).

- El [WideControl](./widecontrol-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la vista. En el ejemplo anterior, la vista está diseñada para mostrar el [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propiedad.

Para obtener un ejemplo de un archivo de formato completo que define una vista amplia simple, vea [vista amplia (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Proporcionar las definiciones para la vista ampliada

Vista amplia puede proporcionar una o varias definiciones mediante el uso de los elementos secundarios de la [WideControl](./widecontrol-element-format.md) elemento. Normalmente, una vista tendrá una única definición. En el ejemplo siguiente, la vista proporciona una única definición que muestra el valor de la [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propiedad. El valor de una propiedad o el valor de una secuencia de comandos (no se muestra en el ejemplo), puede mostrar una vista amplia.

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

Los siguientes elementos XML pueden usarse para proporcionar las definiciones para una vista amplia:

- El [WideControl](./widecontrol-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la vista.

- El [AutoSize](./autosize-element-for-widecontrol-format.md) elemento especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos. Este elemento es opcional.

- El [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento especifica el número de columnas mostradas en la vista ampliada. Este elemento es opcional.

- El [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento proporciona las definiciones de la vista. En la mayoría de los casos, una vista tendrá una única definición. Este elemento es necesario.

- El [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento proporciona una definición de la vista. Al menos un [WideEntry](./wideentry-element-for-widecontrol-format.md) es necesario; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar. En la mayoría de los casos, una vista tendrá una única definición.

- El [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento especifica los objetos que se muestran en una definición específica. Este elemento es opcional y solo es necesario cuando definir varios [WideEntry](./wideentry-element-for-widecontrol-format.md) elementos que muestran los distintos objetos.

- El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento especifica los datos que se muestran la vista. A diferencia de otros tipos de vistas, un gran control puede mostrar un único elemento.

- El [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra la vista. Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.

- El [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra la vista. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

- El [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento especifica un patrón que se usa para mostrar los datos. Este elemento es opcional.

Para obtener un ejemplo de un archivo de formato completo que define una definición de vista ampliada, vea [vista amplia (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definir los objetos que utilizan la vista ampliada

Hay dos maneras de definir qué objetos de .NET usan la vista ampliada. Puede usar el [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir los objetos que se pueden mostrar todas las definiciones de la vista, o bien puede usar el [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento para definir qué objetos se muestran mediante un definición específica de la vista. En la mayoría de los casos, una vista tiene una única definición, por lo que normalmente se definen los objetos mediante el [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

El ejemplo siguiente muestra cómo se definen los objetos que se muestran utilizando la vista amplia el [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) elementos. No hay ningún límite al número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que puede especificar y su orden no es significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista ampliada:

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista ampliada.

- El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica .NET que se muestra la vista. Se requiere el nombre de tipo .NET completo. Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

Para obtener un ejemplo de un archivo de formato completo, vea [vista amplia (Basic)](./wide-view-basic.md).

En el ejemplo siguiente se usa el [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Usar conjuntos de selección donde haya un conjunto de objetos que se muestran usando varias vistas, como cuando se define una vista amplia y una vista de tabla para los mismos objetos relacionados. Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista ampliada:

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista ampliada.

- El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento especifica un conjunto de objetos que se puede mostrar la vista. Debe especificar al menos un conjunto de selección o tipo de la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

El ejemplo siguiente muestra cómo definir los objetos mostrados por una definición específica de la vista ampliada mediante el [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento. Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que se especifica cuando se usa la definición. Para obtener más información acerca de cómo crear una selección de las condiciones, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Los siguientes elementos XML pueden usarse para especificar los objetos usados por una definición específica de la vista ampliada:

- El [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento define los objetos que se muestran en la definición.

- El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica .NET que se muestra la definición. Cuando se usa este elemento es necesario el nombre de tipo .NET completo. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (no mostrado) especifica un conjunto de objetos que se pueden mostrar por esta definición. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) elemento (no mostrado) especifica una condición que debe existir para que esta definición para usarse. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar. Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Muestra los grupos de objetos en una vista amplia

Puede separar los objetos que se muestran en la vista ampliada en grupos. Esto no significa que definir un grupo, solo que PowerShell de Windows se inicia un nuevo grupo cada vez que cambia el valor de una propiedad específica o un script. En el ejemplo siguiente, se inicia un nuevo grupo cada vez que el valor de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) los cambios de propiedad.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Los siguientes elementos XML se usan para definir cuando se inicia un grupo:

- El [GroupBy](./groupby-element-for-view-format.md) elemento define la propiedad o el script que se inicia el nuevo grupo y define cómo se muestra el grupo.

- El [PropertyName](./propertyname-element-for-groupby-format.md) elemento especifica la propiedad que inicia un nuevo grupo cada vez que cambia su valor. Debe especificar una propiedad o un script para iniciar el grupo, pero no se puede especificar ambos.

- El [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor. Debe especificar un script o una propiedad para iniciar el grupo, pero no se puede especificar ambos.

- El [etiqueta](./label-element-for-groupby-format.md) elemento define una etiqueta que se muestra al principio de cada grupo. Además del texto especificado por este elemento, Windows PowerShell muestra el valor que desencadena el nuevo grupo y agrega una línea en blanco antes y después de la etiqueta. Este elemento es opcional.

- El [control personalizado](./customcontrol-element-for-groupby-format.md) elemento define un control que se usa para mostrar los datos. Este elemento es opcional.

- El [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento especifica un común o control que se usa para mostrar los datos de vista. Este elemento es opcional.

Para obtener un ejemplo de un archivo de formato completo que define los grupos, consulte [vista amplia (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Usar cadenas de formato

Las cadenas de formato se pueden agregar a una vista amplia para definir cómo se muestran los datos. El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Los siguientes elementos XML pueden usarse para especificar un patrón de formato:

- El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento especifica los datos que se muestran la vista.

- El [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra la vista. Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.

- El [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista

- El [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

En el ejemplo siguiente, la `ToString` método se llama para dar formato al valor de la secuencia de comandos. Las secuencias de comandos pueden llamar a cualquier método de un objeto. Por lo tanto, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida de la secuencia de comandos.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

El siguiente elemento XML puede usarse para llamar a la `ToString` método:

- El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento especifica los datos que se muestran la vista.

- El [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

## <a name="see-also"></a>Véase también

[Vista amplia (Basic)](./wide-view-basic.md)

[Vista amplia (GroupBy)](./wide-view-groupby.md)

[Escribir un archivo de formato de PowerShell](./writing-a-powershell-formatting-file.md)
