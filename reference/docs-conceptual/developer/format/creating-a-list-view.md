---
title: Crear una vista de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368984"
---
# <a name="creating-a-list-view"></a>Creación de una vista de lista

Una vista de lista muestra los datos en una sola columna (en orden secuencial). Los datos que se muestran en la lista pueden ser el valor de una propiedad de .NET o el valor de un script.

## <a name="a-list-view-display"></a>Visualización de una vista de lista

La siguiente salida muestra cómo Windows PowerShell muestra las propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) . En este ejemplo, se devolvieron tres objetos, donde cada objeto está separado del objeto anterior en una línea en blanco.

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

## <a name="defining-the-list-view"></a>Definir la vista de lista

El siguiente XML muestra el esquema de la vista de lista para mostrar varias propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) (objeto). Debe especificar cada propiedad que desea que se muestre en la vista de lista.

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

Los siguientes elementos XML se utilizan para definir una vista de lista:

- El elemento de [vista](./view-element-format.md) es el elemento primario de la vista de lista. (Es el mismo elemento primario para las vistas de tabla, ancho y control personalizado).

- El elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista. Este elemento es necesario para todas las vistas.

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista. Este elemento es obligatorio.

- El elemento [GroupBy](./groupby-element-for-view-format.md) define cuándo se muestra un nuevo grupo de objetos. Se inicia un nuevo grupo siempre que cambia el valor de una propiedad o un script específicos. Este elemento es opcional.

- El elemento [Controls](./controls-element-for-view-format.md) define los controles personalizados que se definen en la vista de lista. Los controles ofrecen una manera de especificar mejor cómo se muestran los datos. Este elemento es opcional. Una vista puede definir sus propios controles personalizados o puede usar controles comunes que se pueden usar en cualquier vista del archivo de formato. Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).

- El elemento [ListControl](./listcontrol-element-format.md) define lo que se muestra en la vista y cómo se le da formato. Al igual que todas las demás vistas, una vista de lista puede mostrar los valores de las propiedades de objeto o de los valores generados por el script.

Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea la [vista de lista (básica)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Proporcionar definiciones para la vista de lista

Las vistas de lista pueden proporcionar una o más definiciones mediante los elementos secundarios del elemento [ListControl](./listcontrol-element-format.md) . Normalmente, una vista solo tendrá una definición. En el ejemplo siguiente, la vista proporciona una definición única que muestra varias propiedades de [System. Diagnostics. Process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) (objeto). Una vista de lista puede mostrar el valor de una propiedad o el valor de un script (no se muestra en el ejemplo).

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

Los siguientes elementos XML se pueden usar para proporcionar definiciones para una vista de lista:

- El elemento [ListControl](./listcontrol-element-format.md) y sus elementos secundarios definen lo que se muestra en la vista.

- El elemento [ListEntries](./listentries-element-for-listcontrol-format.md) proporciona las definiciones de la vista. En la mayoría de los casos, una vista solo tendrá una definición. Este elemento es obligatorio.

- El elemento [ListEntry](./listentry-element-for-listcontrol-format.md) proporciona una definición de la vista. Se requiere al menos una [ListEntry](./listentry-element-for-listcontrol-format.md) ; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar. En la mayoría de los casos, una vista solo tendrá una definición.

- El elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) especifica los objetos que se muestran en una definición específica. Este elemento es opcional y solo es necesario cuando se definen varios elementos [ListEntry](./listentry-element-for-listcontrol-format.md) que muestran objetos diferentes.

- El elemento [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) especifica las propiedades y los scripts cuyos valores se muestran en las filas de la vista de lista.

- El elemento [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) especifica una propiedad o un script cuyo valor se muestra en una fila de la vista de lista. Una vista de lista debe especificar al menos una propiedad o un script. No hay ningún límite máximo en el número de filas que se pueden especificar.

- El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) especifica la propiedad cuyo valor se muestra en la fila. Debe especificar una propiedad o un script, pero no puede especificar ambos.

- El elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) especifica el script cuyo valor se muestra en la fila. Debe especificar un script o una propiedad, pero no puede especificar ambos.

- El elemento [Label](./label-element-for-listitem-for-listcontrol-format.md) especifica la etiqueta que se muestra a la izquierda de la propiedad o el valor de script de la fila. Este elemento es opcional. Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script. Para obtener un ejemplo completo, vea la [vista de lista (etiquetas)](./list-view-labels.md).

- El elemento [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) especifica una condición que debe existir para que se muestre la fila. Para obtener más información sobre cómo agregar condiciones a la vista de lista, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md). Este elemento es opcional.

- El elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) especifica un patrón que se utiliza para mostrar el valor de la propiedad o el script. Este elemento es opcional.

Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea la [vista de lista (básica)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definir los objetos que usan la vista de lista

Hay dos maneras de definir qué objetos .NET usan la vista de lista. Puede usar el elemento [ViewSelectedBy](./viewselectedby-element-format.md) para definir los objetos que se pueden mostrar en todas las definiciones de la vista, o puede usar el elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) para definir qué objetos se muestran en una definición específica de la vista. En la mayoría de los casos, una vista solo tiene una definición, por lo que los objetos se definen normalmente mediante el elemento [ViewSelectedBy](./viewselectedby-element-format.md) .

En el ejemplo siguiente se muestra cómo definir los objetos que se muestran en la vista de lista mediante los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) . No hay ningún límite en el número de elementos [TypeName](./typename-element-for-viewselectedby-format.md) que se pueden especificar y su orden no es significativo.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista de lista:

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.

- El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el objeto .net que se muestra en la vista. El nombre completo del tipo .NET es obligatorio. Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.

Para obtener un ejemplo de un archivo de formato completo, vea [vista de lista (básico)](./list-view-basic.md).

En el ejemplo siguiente se usan los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Use conjuntos de selección en los que tenga un conjunto relacionado de objetos que se muestran mediante varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos. Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista de lista:

- El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.

- El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos que se pueden mostrar en la vista. Debe especificar al menos un conjunto o tipo de selección para la vista, pero no se puede especificar un número máximo de elementos.

En el ejemplo siguiente se muestra cómo definir los objetos mostrados por una definición específica de la vista de lista mediante el elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) . Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que especifica cuándo se usa la definición. Para obtener más información sobre cómo crear condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en una definición específica de la vista de lista:

- El elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) define qué objetos se muestran en la definición.

- El elemento [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) especifica el objeto .net que se muestra en la definición. Al usar este elemento, se requiere el nombre completo del tipo .NET. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica un conjunto de objetos que se pueden mostrar en esta definición. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.

- El elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica una condición que debe existir para que se use esta definición. Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar. Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Mostrar grupos de objetos en una vista de lista

Puede separar los objetos que se muestran en la vista de lista en grupos. Esto no significa que defina un grupo, solo que Windows PowerShell inicie un nuevo grupo siempre que cambie el valor de una propiedad o un script específicos. En el ejemplo siguiente, se inicia un nuevo grupo siempre que cambia el valor de la propiedad [System. ServiceProcess. ServiceController. serviceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .

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

Para obtener un ejemplo de un archivo de formato completo que define grupos, vea la [vista de lista (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Usar cadenas de formato

Las cadenas de formato se pueden agregar a una vista para definir mejor cómo se muestran los datos. En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Los siguientes elementos XML se pueden usar para especificar un modelo de formato:

- El elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) especifica los datos que se muestran en la vista.

- El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) especifica la propiedad cuyo valor se muestra en la vista. Debe especificar una propiedad o un script, pero no puede especificar ambos.

- El elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.

- El elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista. Debe especificar un script o una propiedad, pero no puede especificar ambos.

En el ejemplo siguiente, se llama al método `ToString` para dar formato al valor del script. Los scripts pueden llamar a cualquier método de un objeto. Por consiguiente, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida del script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

El siguiente elemento XML se puede usar para llamar al método `ToString`:

- El elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) especifica los datos que se muestran en la vista.

- El elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista. Debe especificar un script o una propiedad, pero no puede especificar ambos.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
