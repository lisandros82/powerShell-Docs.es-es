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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861581"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="b1358-102">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="b1358-102">Creating a List View</span></span>

<span data-ttu-id="b1358-103">Una vista de lista muestra los datos en una sola columna (en orden secuencial).</span><span class="sxs-lookup"><span data-stu-id="b1358-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="b1358-104">Los datos mostrados en la lista pueden ser el valor de una propiedad .NET o el valor de una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1358-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="b1358-105">Una presentación de la vista de lista</span><span class="sxs-lookup"><span data-stu-id="b1358-105">A List View Display</span></span>

<span data-ttu-id="b1358-106">¿La salida siguiente muestra cómo Windows PowerShell muestra las propiedades de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) los objetos devueltos por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1358-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="b1358-107">En este ejemplo, se devolvieron tres objetos, con cada objeto separado del objeto anterior mediante una línea en blanco.</span><span class="sxs-lookup"><span data-stu-id="b1358-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="b1358-108">Define la vista de lista</span><span class="sxs-lookup"><span data-stu-id="b1358-108">Defining the List View</span></span>

<span data-ttu-id="b1358-109">¿El siguiente XML muestra el esquema de vista de lista para mostrar varias propiedades de la [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="b1358-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="b1358-110">Debe especificar cada propiedad que desea que aparezca en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="b1358-111">Los siguientes elementos XML se usan para definir una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="b1358-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="b1358-112">El [vista](./view-element-format.md) elemento es el elemento primario de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="b1358-113">(Esto es el mismo elemento primario de la tabla, las vistas de control ancho y personalizadas).</span><span class="sxs-lookup"><span data-stu-id="b1358-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="b1358-114">El [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="b1358-115">Este elemento es necesario para todas las vistas.</span><span class="sxs-lookup"><span data-stu-id="b1358-115">This element is required for all views.</span></span>

- <span data-ttu-id="b1358-116">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="b1358-117">Este elemento es necesario.</span><span class="sxs-lookup"><span data-stu-id="b1358-117">This element is required.</span></span>

- <span data-ttu-id="b1358-118">El [GroupBy](./groupby-element-for-view-format.md) elemento define cuando se muestre un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="b1358-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="b1358-119">Cada vez que cambia el valor de una propiedad específica o un script, se inicia un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="b1358-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b1358-120">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-120">This element is optional.</span></span>

- <span data-ttu-id="b1358-121">El [controles](./controls-element-for-view-format.md) elemento define los controles personalizados que se definen mediante la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="b1358-122">Los controles ofrecen una manera de especificar cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="b1358-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="b1358-123">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-123">This element is optional.</span></span> <span data-ttu-id="b1358-124">Una vista puede definir sus propios controles personalizados, o puede usar controles comunes que pueden usarse en cualquier vista en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="b1358-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="b1358-125">Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="b1358-126">El [ListControl](./listcontrol-element-format.md) elemento define lo que se muestra en la vista y cómo se da formato.</span><span class="sxs-lookup"><span data-stu-id="b1358-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="b1358-127">Al igual que todas las demás vistas, una vista de lista puede mostrar los valores de las propiedades del objeto o los valores generados por script.</span><span class="sxs-lookup"><span data-stu-id="b1358-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="b1358-128">Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea [vista de lista (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="b1358-129">Proporcionar las definiciones para la vista de lista</span><span class="sxs-lookup"><span data-stu-id="b1358-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="b1358-130">Vistas de lista pueden proporcionar una o varias definiciones mediante el uso de los elementos secundarios de la [ListControl](./listcontrol-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b1358-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="b1358-131">Normalmente, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="b1358-132">¿En el ejemplo siguiente, la vista proporciona una única definición que muestra varias propiedades de la [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="b1358-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="b1358-133">El valor de una propiedad o el valor de una secuencia de comandos (no se muestra en el ejemplo), puede mostrar una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="b1358-134">Los siguientes elementos XML pueden usarse para proporcionar las definiciones para una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="b1358-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="b1358-135">El [ListControl](./listcontrol-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="b1358-136">El [ListEntries](./listentries-element-for-listcontrol-format.md) elemento proporciona las definiciones de la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="b1358-137">En la mayoría de los casos, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="b1358-138">Este elemento es necesario.</span><span class="sxs-lookup"><span data-stu-id="b1358-138">This element is required.</span></span>

- <span data-ttu-id="b1358-139">El [ListEntry](./listentry-element-for-listcontrol-format.md) elemento proporciona una definición de la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="b1358-140">Al menos un [ListEntry](./listentry-element-for-listcontrol-format.md) es necesario; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="b1358-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="b1358-141">En la mayoría de los casos, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="b1358-142">El [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento especifica los objetos que se muestran en una definición específica.</span><span class="sxs-lookup"><span data-stu-id="b1358-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="b1358-143">Este elemento es opcional y solo es necesario cuando definir varios [ListEntry](./listentry-element-for-listcontrol-format.md) elementos que muestran los distintos objetos.</span><span class="sxs-lookup"><span data-stu-id="b1358-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="b1358-144">El [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) elemento especifica las propiedades y los scripts cuyos valores se muestran en las filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="b1358-145">El [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elemento especifica una propiedad o un script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="b1358-146">Una vista de lista debe especificar al menos una propiedad o una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1358-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="b1358-147">No hay ningún límite máximo para el número de filas que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b1358-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="b1358-148">El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento especifica la propiedad cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="b1358-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="b1358-149">Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b1358-150">El [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="b1358-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="b1358-151">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="b1358-152">El [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) elemento especifica la etiqueta que aparece a la izquierda del valor de propiedad o un script en la fila.</span><span class="sxs-lookup"><span data-stu-id="b1358-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="b1358-153">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-153">This element is optional.</span></span> <span data-ttu-id="b1358-154">Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="b1358-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="b1358-155">Para obtener un ejemplo completo, vea [vista de lista (etiquetas)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="b1358-156">El [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elemento especifica una condición que debe existir la fila que se va a mostrarse.</span><span class="sxs-lookup"><span data-stu-id="b1358-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="b1358-157">Para obtener más información sobre cómo agregar condiciones a la vista de lista, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="b1358-158">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-158">This element is optional.</span></span>

- <span data-ttu-id="b1358-159">El [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón que se usa para mostrar el valor de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="b1358-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="b1358-160">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-160">This element is optional.</span></span>

<span data-ttu-id="b1358-161">Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea [vista de lista (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="b1358-162">Definir los objetos que utilizan la vista de lista</span><span class="sxs-lookup"><span data-stu-id="b1358-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="b1358-163">Hay dos maneras de definir qué objetos de .NET utilizan la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="b1358-164">Puede usar el [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir los objetos que se pueden mostrar todas las definiciones de la vista, o bien puede usar el [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir qué objetos se muestran mediante un definición específica de la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="b1358-165">En la mayoría de los casos, una vista tiene una única definición, por lo que normalmente se definen los objetos mediante el [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b1358-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="b1358-166">El ejemplo siguiente muestra cómo se definen los objetos que se muestran en la vista de lista mediante el [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="b1358-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b1358-167">No hay ningún límite al número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que puede especificar y su orden no es significativo.</span><span class="sxs-lookup"><span data-stu-id="b1358-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="b1358-168">Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="b1358-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="b1358-169">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="b1358-170">El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica el objeto .NET que se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="b1358-171">Se requiere el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="b1358-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="b1358-172">Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b1358-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b1358-173">Para obtener un ejemplo de un archivo de formato completo, vea [vista de lista (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="b1358-174">En el ejemplo siguiente se usa el [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="b1358-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b1358-175">Usar conjuntos de selección donde haya un conjunto de objetos que se muestran usando varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="b1358-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="b1358-176">Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="b1358-177">Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="b1358-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="b1358-178">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b1358-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="b1358-179">El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento especifica un conjunto de objetos que se puede mostrar la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="b1358-180">Debe especificar al menos un conjunto de selección o tipo de la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b1358-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b1358-181">El ejemplo siguiente muestra cómo definir los objetos mostrados por una definición específica de la vista de lista mediante el [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b1358-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="b1358-182">Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que se especifica cuando se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="b1358-183">Para obtener más información acerca de cómo crear una selección de las condiciones, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="b1358-184">Los siguientes elementos XML pueden usarse para especificar los objetos usados por una definición específica de la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="b1358-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="b1358-185">El [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento define los objetos que se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="b1358-186">El [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento especifica el objeto .NET que se muestra la definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="b1358-187">Cuando se usa este elemento, se requiere el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="b1358-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="b1358-188">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b1358-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b1358-189">El [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica un conjunto de objetos que se pueden mostrar por esta definición.</span><span class="sxs-lookup"><span data-stu-id="b1358-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="b1358-190">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b1358-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b1358-191">El [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica una condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="b1358-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b1358-192">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b1358-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="b1358-193">Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="b1358-194">Muestra los grupos de objetos en una vista de lista</span><span class="sxs-lookup"><span data-stu-id="b1358-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="b1358-195">Puede separar los objetos que se muestran en la vista de lista en grupos.</span><span class="sxs-lookup"><span data-stu-id="b1358-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="b1358-196">Esto no significa que definir un grupo, solo que PowerShell de Windows se inicia un nuevo grupo cada vez que cambia el valor de una propiedad específica o un script.</span><span class="sxs-lookup"><span data-stu-id="b1358-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b1358-197">En el ejemplo siguiente, se inicia un nuevo grupo cada vez que el valor de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) los cambios de propiedad.</span><span class="sxs-lookup"><span data-stu-id="b1358-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="b1358-198">Los siguientes elementos XML se usan para definir cuando se inicia un grupo:</span><span class="sxs-lookup"><span data-stu-id="b1358-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="b1358-199">El [GroupBy](./groupby-element-for-view-format.md) elemento define la propiedad o el script que se inicia el nuevo grupo y define cómo se muestra el grupo.</span><span class="sxs-lookup"><span data-stu-id="b1358-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="b1358-200">El [PropertyName](./propertyname-element-for-groupby-format.md) elemento especifica la propiedad que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="b1358-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="b1358-201">Debe especificar una propiedad o un script para iniciar el grupo, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="b1358-202">El [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="b1358-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="b1358-203">Debe especificar un script o una propiedad para iniciar el grupo, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="b1358-204">El [etiqueta](./label-element-for-groupby-format.md) elemento define una etiqueta que se muestra al principio de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="b1358-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="b1358-205">Además del texto especificado por este elemento, Windows PowerShell muestra el valor que desencadena el nuevo grupo y agrega una línea en blanco antes y después de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="b1358-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="b1358-206">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-206">This element is optional.</span></span>

- <span data-ttu-id="b1358-207">El [control personalizado](./customcontrol-element-for-groupby-format.md) elemento define un control que se usa para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="b1358-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="b1358-208">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-208">This element is optional.</span></span>

- <span data-ttu-id="b1358-209">El [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento especifica un común o control que se usa para mostrar los datos de vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="b1358-210">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b1358-210">This element is optional.</span></span>

<span data-ttu-id="b1358-211">Para obtener un ejemplo de un archivo de formato completo que define los grupos, consulte [vista de lista (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="b1358-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="b1358-212">Usar cadenas de formato</span><span class="sxs-lookup"><span data-stu-id="b1358-212">Using Format Strings</span></span>

<span data-ttu-id="b1358-213">Las cadenas de formato se pueden agregar a una vista para definir cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="b1358-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="b1358-214">El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.</span><span class="sxs-lookup"><span data-stu-id="b1358-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="b1358-215">Los siguientes elementos XML pueden usarse para especificar un patrón de formato:</span><span class="sxs-lookup"><span data-stu-id="b1358-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="b1358-216">El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento especifica los datos que se muestran la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="b1358-217">El [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento especifica la propiedad cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="b1358-218">Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b1358-219">El [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="b1358-220">El [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b1358-221">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="b1358-222">En el ejemplo siguiente, la `ToString` método se llama para dar formato al valor de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1358-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="b1358-223">Las secuencias de comandos pueden llamar a cualquier método de un objeto.</span><span class="sxs-lookup"><span data-stu-id="b1358-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="b1358-224">Por lo tanto, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1358-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="b1358-225">El siguiente elemento XML puede usarse para llamar a la `ToString` método:</span><span class="sxs-lookup"><span data-stu-id="b1358-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="b1358-226">El [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento especifica los datos que se muestran la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="b1358-227">El [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b1358-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b1358-228">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b1358-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1358-229">Véase también</span><span class="sxs-lookup"><span data-stu-id="b1358-229">See Also</span></span>

[<span data-ttu-id="b1358-230">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b1358-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
