---
title: Creación de una vista de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066862"
---
# <a name="creating-a-list-view"></a>Creación de una vista de lista

Una vista de lista muestra los datos en una sola columna (en orden secuencial). Los datos mostrados en la lista pueden ser el valor de una propiedad .NET o el valor de una secuencia de comandos.

## <a name="a-list-view-display"></a>Una presentación de la vista de lista

¿La salida siguiente muestra cómo Windows PowerShell muestra las propiedades de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. En este ejemplo, se devolvieron tres objetos, con cada objeto separado del objeto anterior mediante una línea en blanco.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Define la vista de lista

¿El siguiente XML muestra el esquema de vista de lista para mostrar varias propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto. Debe especificar cada propiedad que desea que aparezca en la vista de lista.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Los siguientes elementos XML se usan para definir una vista de lista:

- El [vista](./view-element-format.md) elemento es el elemento primario de la vista de lista. (Esto es el mismo elemento primario de la tabla, las vistas de control ancho y personalizadas).

- El [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista. Este elemento es necesario para todas las vistas.

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista. Este elemento es necesario.

- El [GroupBy](./groupby-element-for-view-format.md) elemento define cuando se muestre un nuevo grupo de objetos. Cada vez que cambia el valor de una propiedad específica o un script, se inicia un nuevo grupo. Este elemento es opcional.

- El [controles](./controls-element-for-view-format.md) elemento define los controles personalizados que se definen mediante la vista de lista. Los controles ofrecen una manera de especificar cómo se muestran los datos. Este elemento es opcional. Una vista puede definir sus propios controles personalizados, o puede usar controles comunes que pueden usarse en cualquier vista en el archivo de formato. Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).

- El [ListControl](./listcontrol-element-format.md) elemento define lo que se muestra en la vista y cómo se da formato. Al igual que todas las demás vistas, una vista de lista puede mostrar los valores de las propiedades del objeto o los valores generados por script.

Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea [vista de lista (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Proporcionar las definiciones para la vista de lista

Vistas de lista pueden proporcionar una o varias definiciones mediante el uso de los elementos secundarios de la [ListControl](./listcontrol-element-format.md) elemento. Normalmente, una vista tendrá una única definición. ¿En el ejemplo siguiente, la vista proporciona una única definición que muestra varias propiedades de la [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto. El valor de una propiedad o el valor de una secuencia de comandos (no se muestra en el ejemplo), puede mostrar una vista de lista.

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Los siguientes elementos XML pueden usarse para proporcionar las definiciones para una vista de lista:

- El [ListControl](./listcontrol-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la vista.

- El [ListEntries](./listentries-element-for-listcontrol-format.md) elemento proporciona las definiciones de la vista. En la mayoría de los casos, una vista tendrá una única definición. Este elemento es necesario.

- El [ListEntry](./listentry-element-for-listcontrol-format.md) elemento proporciona una definición de la vista. Al menos un [ListEntry](./listentry-element-for-listcontrol-format.md) es necesario; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar. En la mayoría de los casos, una vista tendrá una única definición.

- El [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento especifica los objetos que se muestran en una definición específica. Este elemento es opcional y solo es necesario cuando definir varios [ListEntry](./listentry-element-for-listcontrol-format.md) elementos que muestran los distintos objetos.

- El [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) elemento especifica las propiedades y los scripts cuyos valores se muestran en las filas de la vista de lista.

- El [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elemento especifica una propiedad o un script cuyo valor se muestra en una fila de la vista de lista. Una vista de lista debe especificar al menos una propiedad o una secuencia de comandos. No hay ningún límite máximo para el número de filas que se pueden especificar.

- El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento especifica la propiedad cuyo valor se muestra en la fila. Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.

- El [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra en la fila. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

- El [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) elemento especifica la etiqueta que aparece a la izquierda del valor de propiedad o un script en la fila. Este elemento es opcional. Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script. Para obtener un ejemplo completo, vea [vista de lista (etiquetas)](./list-view-labels.md).

- El [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elemento especifica una condición que debe existir la fila que se va a mostrarse. Para obtener más información sobre cómo agregar condiciones a la vista de lista, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md). Este elemento es opcional.

- El [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón que se usa para mostrar el valor de la propiedad o el script. Este elemento es opcional.

Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea [vista de lista (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definir los objetos que utilizan la vista de lista

Hay dos maneras de definir qué objetos de .NET utilizan la vista de lista. Puede usar el [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir los objetos que se pueden mostrar todas las definiciones de la vista, o bien puede usar el [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir qué objetos se muestran mediante un definición específica de la vista. En la mayoría de los casos, una vista tiene una única definición, por lo que normalmente se definen los objetos mediante el [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

El ejemplo siguiente muestra cómo se definen los objetos que se muestran en la vista de lista mediante el [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) elementos. No hay ningún límite al número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que puede especificar y su orden no es significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de lista:

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.

- El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica el objeto .NET que se muestra la vista. Se requiere el nombre de tipo .NET completo. Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

Para obtener un ejemplo de un archivo de formato completo, vea [vista de lista (Basic)](./list-view-basic.md).

En el ejemplo siguiente se usa el [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Usar conjuntos de selección donde haya un conjunto de objetos que se muestran usando varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos relacionados. Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de lista:

- El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.

- El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento especifica un conjunto de objetos que se puede mostrar la vista. Debe especificar al menos un conjunto de selección o tipo de la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

El ejemplo siguiente muestra cómo definir los objetos mostrados por una definición específica de la vista de lista mediante el [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento. Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que se especifica cuando se usa la definición. Para obtener más información acerca de cómo crear una selección de las condiciones, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Los siguientes elementos XML pueden usarse para especificar los objetos usados por una definición específica de la vista de lista:

- El [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento define los objetos que se muestran en la definición.

- El [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento especifica el objeto .NET que se muestra la definición. Cuando se usa este elemento, se requiere el nombre de tipo .NET completo. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica un conjunto de objetos que se pueden mostrar por esta definición. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica una condición que debe existir para que esta definición para usarse. Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar. Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Muestra los grupos de objetos en una vista de lista

Puede separar los objetos que se muestran en la vista de lista en grupos. Esto no significa que definir un grupo, solo que PowerShell de Windows se inicia un nuevo grupo cada vez que cambia el valor de una propiedad específica o un script. En el ejemplo siguiente, se inicia un nuevo grupo cada vez que el valor de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) los cambios de propiedad.

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

Para obtener un ejemplo de un archivo de formato completo que define los grupos, consulte [vista de lista (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Usar cadenas de formato

Las cadenas de formato se pueden agregar a una vista para definir cómo se muestran los datos. El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Los siguientes elementos XML pueden usarse para especificar un patrón de formato:

- El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento especifica los datos que se muestran la vista.

- El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento especifica la propiedad cuyo valor se muestra la vista. Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.

- El [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.

- El [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

En el ejemplo siguiente, la `ToString` método se llama para dar formato al valor de la secuencia de comandos. Las secuencias de comandos pueden llamar a cualquier método de un objeto. Por lo tanto, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida de la secuencia de comandos.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

El siguiente elemento XML puede usarse para llamar a la `ToString` método:

- El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento especifica los datos que se muestran la vista.

- El [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista. Debe especificar un script o una propiedad, pero no se puede especificar ambos.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
