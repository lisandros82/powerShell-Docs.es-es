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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368984"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="d0cf1-102">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0cf1-102">Creating a List View</span></span>

<span data-ttu-id="d0cf1-103">Una vista de lista muestra los datos en una sola columna (en orden secuencial).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="d0cf1-104">Los datos que se muestran en la lista pueden ser el valor de una propiedad de .NET o el valor de un script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="d0cf1-105">Visualización de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0cf1-105">A List View Display</span></span>

<span data-ttu-id="d0cf1-106">La siguiente salida muestra cómo Windows PowerShell muestra las propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objetos devueltos por el cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="d0cf1-107">En este ejemplo, se devolvieron tres objetos, donde cada objeto está separado del objeto anterior en una línea en blanco.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="d0cf1-108">Definir la vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0cf1-108">Defining the List View</span></span>

<span data-ttu-id="d0cf1-109">El siguiente XML muestra el esquema de la vista de lista para mostrar varias propiedades de [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) (objeto).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="d0cf1-110">Debe especificar cada propiedad que desea que se muestre en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="d0cf1-111">Los siguientes elementos XML se utilizan para definir una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="d0cf1-112">El elemento de [vista](./view-element-format.md) es el elemento primario de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="d0cf1-113">(Es el mismo elemento primario para las vistas de tabla, ancho y control personalizado).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="d0cf1-114">El elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="d0cf1-115">Este elemento es necesario para todas las vistas.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-115">This element is required for all views.</span></span>

- <span data-ttu-id="d0cf1-116">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="d0cf1-117">Se requiere el elemento.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-117">This element is required.</span></span>

- <span data-ttu-id="d0cf1-118">El elemento [GroupBy](./groupby-element-for-view-format.md) define cuándo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="d0cf1-119">Se inicia un nuevo grupo siempre que cambia el valor de una propiedad o un script específicos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d0cf1-120">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-120">This element is optional.</span></span>

- <span data-ttu-id="d0cf1-121">El elemento [Controls](./controls-element-for-view-format.md) define los controles personalizados que se definen en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="d0cf1-122">Los controles ofrecen una manera de especificar mejor cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="d0cf1-123">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-123">This element is optional.</span></span> <span data-ttu-id="d0cf1-124">Una vista puede definir sus propios controles personalizados o puede usar controles comunes que se pueden usar en cualquier vista del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="d0cf1-125">Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="d0cf1-126">El elemento [ListControl](./listcontrol-element-format.md) define lo que se muestra en la vista y cómo se le da formato.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="d0cf1-127">Al igual que todas las demás vistas, una vista de lista puede mostrar los valores de las propiedades de objeto o de los valores generados por el script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="d0cf1-128">Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea la [vista de lista (básica)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="d0cf1-129">Proporcionar definiciones para la vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0cf1-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="d0cf1-130">Las vistas de lista pueden proporcionar una o más definiciones mediante los elementos secundarios del elemento [ListControl](./listcontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="d0cf1-131">Normalmente, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="d0cf1-132">En el ejemplo siguiente, la vista proporciona una definición única que muestra varias propiedades de [System. Diagnostics. Process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) (objeto).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="d0cf1-133">Una vista de lista puede mostrar el valor de una propiedad o el valor de un script (no se muestra en el ejemplo).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="d0cf1-134">Los siguientes elementos XML se pueden usar para proporcionar definiciones para una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="d0cf1-135">El elemento [ListControl](./listcontrol-element-format.md) y sus elementos secundarios definen lo que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="d0cf1-136">El elemento [ListEntries](./listentries-element-for-listcontrol-format.md) proporciona las definiciones de la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="d0cf1-137">En la mayoría de los casos, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="d0cf1-138">Se requiere el elemento.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-138">This element is required.</span></span>

- <span data-ttu-id="d0cf1-139">El elemento [ListEntry](./listentry-element-for-listcontrol-format.md) proporciona una definición de la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="d0cf1-140">Se requiere al menos una [ListEntry](./listentry-element-for-listcontrol-format.md) ; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="d0cf1-141">En la mayoría de los casos, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="d0cf1-142">El elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) especifica los objetos que se muestran en una definición específica.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="d0cf1-143">Este elemento es opcional y solo es necesario cuando se definen varios elementos [ListEntry](./listentry-element-for-listcontrol-format.md) que muestran objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="d0cf1-144">El elemento [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) especifica las propiedades y los scripts cuyos valores se muestran en las filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="d0cf1-145">El elemento [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) especifica una propiedad o un script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="d0cf1-146">Una vista de lista debe especificar al menos una propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="d0cf1-147">No hay ningún límite máximo en el número de filas que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="d0cf1-148">El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) especifica la propiedad cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d0cf1-149">Debe especificar una propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d0cf1-150">El elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) especifica el script cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d0cf1-151">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="d0cf1-152">El elemento [Label](./label-element-for-listitem-for-listcontrol-format.md) especifica la etiqueta que se muestra a la izquierda de la propiedad o el valor de script de la fila.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="d0cf1-153">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-153">This element is optional.</span></span> <span data-ttu-id="d0cf1-154">Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="d0cf1-155">Para obtener un ejemplo completo, vea la [vista de lista (etiquetas)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="d0cf1-156">El elemento [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) especifica una condición que debe existir para que se muestre la fila.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="d0cf1-157">Para obtener más información sobre cómo agregar condiciones a la vista de lista, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="d0cf1-158">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-158">This element is optional.</span></span>

- <span data-ttu-id="d0cf1-159">El elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) especifica un patrón que se utiliza para mostrar el valor de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="d0cf1-160">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-160">This element is optional.</span></span>

<span data-ttu-id="d0cf1-161">Para obtener un ejemplo de un archivo de formato completo que define una vista de lista simple, vea la [vista de lista (básica)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="d0cf1-162">Definir los objetos que usan la vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0cf1-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="d0cf1-163">Hay dos maneras de definir qué objetos .NET usan la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="d0cf1-164">Puede usar el elemento [ViewSelectedBy](./viewselectedby-element-format.md) para definir los objetos que se pueden mostrar en todas las definiciones de la vista, o puede usar el elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) para definir qué objetos se muestran en una definición específica de la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="d0cf1-165">En la mayoría de los casos, una vista solo tiene una definición, por lo que los objetos se definen normalmente mediante el elemento [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="d0cf1-166">En el ejemplo siguiente se muestra cómo definir los objetos que se muestran en la vista de lista mediante los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d0cf1-167">No hay ningún límite en el número de elementos [TypeName](./typename-element-for-viewselectedby-format.md) que se pueden especificar y su orden no es significativo.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="d0cf1-168">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="d0cf1-169">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d0cf1-170">El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el objeto .net que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="d0cf1-171">El nombre completo del tipo .NET es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="d0cf1-172">Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d0cf1-173">Para obtener un ejemplo de un archivo de formato completo, vea [vista de lista (básico)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="d0cf1-174">En el ejemplo siguiente se usan los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d0cf1-175">Use conjuntos de selección en los que tenga un conjunto relacionado de objetos que se muestran mediante varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="d0cf1-176">Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="d0cf1-177">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="d0cf1-178">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d0cf1-179">El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos que se pueden mostrar en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="d0cf1-180">Debe especificar al menos un conjunto o tipo de selección para la vista, pero no se puede especificar un número máximo de elementos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d0cf1-181">En el ejemplo siguiente se muestra cómo definir los objetos mostrados por una definición específica de la vista de lista mediante el elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="d0cf1-182">Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que especifica cuándo se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="d0cf1-183">Para obtener más información sobre cómo crear condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="d0cf1-184">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en una definición específica de la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="d0cf1-185">El elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) define qué objetos se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="d0cf1-186">El elemento [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) especifica el objeto .net que se muestra en la definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="d0cf1-187">Al usar este elemento, se requiere el nombre completo del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="d0cf1-188">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d0cf1-189">El elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica un conjunto de objetos que se pueden mostrar en esta definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="d0cf1-190">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d0cf1-191">El elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica una condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d0cf1-192">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="d0cf1-193">Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="d0cf1-194">Mostrar grupos de objetos en una vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0cf1-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="d0cf1-195">Puede separar los objetos que se muestran en la vista de lista en grupos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="d0cf1-196">Esto no significa que defina un grupo, solo que Windows PowerShell inicie un nuevo grupo siempre que cambie el valor de una propiedad o un script específicos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d0cf1-197">En el ejemplo siguiente, se inicia un nuevo grupo siempre que cambia el valor de la propiedad [System. ServiceProcess. ServiceController. serviceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .</span><span class="sxs-lookup"><span data-stu-id="d0cf1-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="d0cf1-198">Los siguientes elementos XML se utilizan para definir cuándo se inicia un grupo:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="d0cf1-199">El elemento [GroupBy](./groupby-element-for-view-format.md) define la propiedad o el script que inicia el nuevo grupo y define cómo se muestra el grupo.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="d0cf1-200">El elemento [PropertyName](./propertyname-element-for-groupby-format.md) especifica la propiedad que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="d0cf1-201">Debe especificar una propiedad o un script para iniciar el grupo, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="d0cf1-202">El elemento [ScriptBlock](./scriptblock-element-for-groupby-format.md) especifica el script que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="d0cf1-203">Debe especificar un script o una propiedad para iniciar el grupo, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="d0cf1-204">El elemento [Label](./label-element-for-groupby-format.md) define una etiqueta que se muestra al principio de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="d0cf1-205">Además del texto especificado por este elemento, Windows PowerShell muestra el valor que desencadenó el nuevo grupo y agrega una línea en blanco antes y después de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="d0cf1-206">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-206">This element is optional.</span></span>

- <span data-ttu-id="d0cf1-207">El elemento [CustomControl](./customcontrol-element-for-groupby-format.md) define un control que se utiliza para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="d0cf1-208">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-208">This element is optional.</span></span>

- <span data-ttu-id="d0cf1-209">El elemento [CustomControlName](./customcontrolname-element-for-groupby-format.md) especifica un control común o de vista que se usa para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="d0cf1-210">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-210">This element is optional.</span></span>

<span data-ttu-id="d0cf1-211">Para obtener un ejemplo de un archivo de formato completo que define grupos, vea la [vista de lista (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf1-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="d0cf1-212">Usar cadenas de formato</span><span class="sxs-lookup"><span data-stu-id="d0cf1-212">Using Format Strings</span></span>

<span data-ttu-id="d0cf1-213">Las cadenas de formato se pueden agregar a una vista para definir mejor cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="d0cf1-214">En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="d0cf1-215">Los siguientes elementos XML se pueden usar para especificar un modelo de formato:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="d0cf1-216">El elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) especifica los datos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="d0cf1-217">El elemento [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) especifica la propiedad cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="d0cf1-218">Debe especificar una propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d0cf1-219">El elemento [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="d0cf1-220">El elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d0cf1-221">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="d0cf1-222">En el ejemplo siguiente, se llama al método `ToString` para dar formato al valor del script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="d0cf1-223">Los scripts pueden llamar a cualquier método de un objeto.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="d0cf1-224">Por consiguiente, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida del script.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="d0cf1-225">El siguiente elemento XML se puede usar para llamar al método `ToString`:</span><span class="sxs-lookup"><span data-stu-id="d0cf1-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="d0cf1-226">El elemento [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) especifica los datos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="d0cf1-227">El elemento [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d0cf1-228">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d0cf1-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0cf1-229">Véase también</span><span class="sxs-lookup"><span data-stu-id="d0cf1-229">See Also</span></span>

[<span data-ttu-id="d0cf1-230">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0cf1-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
