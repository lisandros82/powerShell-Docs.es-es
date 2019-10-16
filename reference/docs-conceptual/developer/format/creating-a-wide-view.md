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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368954"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="661e7-102">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="661e7-102">Creating a Wide View</span></span>

<span data-ttu-id="661e7-103">Una vista amplia muestra un valor único para cada objeto que se muestra.</span><span class="sxs-lookup"><span data-stu-id="661e7-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="661e7-104">El valor mostrado puede ser el valor de una propiedad de objeto .NET o el valor de un script.</span><span class="sxs-lookup"><span data-stu-id="661e7-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="661e7-105">De forma predeterminada, no hay ninguna etiqueta o encabezado para esta vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="661e7-106">Visualización de vista amplia</span><span class="sxs-lookup"><span data-stu-id="661e7-106">A Wide View Display</span></span>

<span data-ttu-id="661e7-107">En el ejemplo siguiente se muestra cómo Windows PowerShell muestra el objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) que devuelve el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cuando su salida se canaliza al cmdlet [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) .</span><span class="sxs-lookup"><span data-stu-id="661e7-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="661e7-108">(De forma predeterminada, el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) devuelve una vista de tabla). En este ejemplo, se usan las dos columnas para mostrar el nombre del proceso para cada objeto devuelto.</span><span class="sxs-lookup"><span data-stu-id="661e7-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="661e7-109">No se muestra el nombre de la propiedad del objeto, solo el valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="661e7-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="661e7-110">Definir la vista amplia</span><span class="sxs-lookup"><span data-stu-id="661e7-110">Defining the Wide View</span></span>

<span data-ttu-id="661e7-111">El XML siguiente muestra el esquema de vista ancha para el objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="661e7-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="661e7-112">Los siguientes elementos XML se utilizan para definir una vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="661e7-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="661e7-113">El elemento de [vista](./view-element-format.md) es el elemento primario de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="661e7-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="661e7-114">(Este es el mismo elemento primario para las vistas de tabla, lista y control personalizado).</span><span class="sxs-lookup"><span data-stu-id="661e7-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="661e7-115">El elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="661e7-116">Este elemento es necesario para todas las vistas.</span><span class="sxs-lookup"><span data-stu-id="661e7-116">This element is required for all views.</span></span>

- <span data-ttu-id="661e7-117">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="661e7-118">Este elemento es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="661e7-118">This element is required.</span></span>

- <span data-ttu-id="661e7-119">El elemento [GroupBy](./groupby-element-for-view-format.md) define cuándo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="661e7-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="661e7-120">Se inicia un nuevo grupo siempre que cambia el valor de una propiedad o un script específicos.</span><span class="sxs-lookup"><span data-stu-id="661e7-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="661e7-121">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-121">This element is optional.</span></span>

- <span data-ttu-id="661e7-122">Los elementos [Controls](./controls-element-for-view-format.md) definen los controles personalizados que se definen en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="661e7-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="661e7-123">Los controles ofrecen una manera de especificar mejor cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="661e7-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="661e7-124">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-124">This element is optional.</span></span> <span data-ttu-id="661e7-125">Una vista puede definir sus propios controles personalizados o puede usar controles comunes que se pueden usar en cualquier vista del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="661e7-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="661e7-126">Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="661e7-127">El elemento [WideControl](./widecontrol-element-format.md) y sus elementos secundarios definen lo que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="661e7-128">En el ejemplo anterior, la vista está diseñada para mostrar la propiedad [System. Diagnostics. Process. processName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="661e7-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="661e7-129">Para obtener un ejemplo de un archivo de formato completo que define una vista ancha sencilla, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="661e7-130">Proporcionar definiciones para la vista amplia</span><span class="sxs-lookup"><span data-stu-id="661e7-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="661e7-131">Las vistas anchas pueden proporcionar una o más definiciones mediante el uso de los elementos secundarios del elemento [WideControl](./widecontrol-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="661e7-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="661e7-132">Normalmente, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="661e7-133">En el ejemplo siguiente, la vista proporciona una única definición que muestra el valor de la propiedad [System. Diagnostics. Process. processName](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="661e7-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="661e7-134">Una vista amplia puede mostrar el valor de una propiedad o el valor de un script (no se muestra en el ejemplo).</span><span class="sxs-lookup"><span data-stu-id="661e7-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="661e7-135">Los siguientes elementos XML se pueden usar para proporcionar definiciones para una vista amplia:</span><span class="sxs-lookup"><span data-stu-id="661e7-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="661e7-136">El elemento [WideControl](./widecontrol-element-format.md) y sus elementos secundarios definen lo que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="661e7-137">El elemento [AutoSize](./autosize-element-for-widecontrol-format.md) especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="661e7-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="661e7-138">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-138">This element is optional.</span></span>

- <span data-ttu-id="661e7-139">El elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) especifica el número de columnas que se muestran en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="661e7-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="661e7-140">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-140">This element is optional.</span></span>

- <span data-ttu-id="661e7-141">El elemento [WideEntries](./wideentries-element-for-widecontrol-format.md) proporciona las definiciones de la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="661e7-142">En la mayoría de los casos, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="661e7-143">Este elemento es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="661e7-143">This element is required.</span></span>

- <span data-ttu-id="661e7-144">El elemento [WideEntry](./wideentry-element-for-widecontrol-format.md) proporciona una definición de la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="661e7-145">Se requiere al menos un [WideEntry](./wideentry-element-for-widecontrol-format.md) ; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="661e7-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="661e7-146">En la mayoría de los casos, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="661e7-147">El elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) especifica los objetos que se muestran en una definición específica.</span><span class="sxs-lookup"><span data-stu-id="661e7-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="661e7-148">Este elemento es opcional y solo es necesario cuando se definen varios elementos [WideEntry](./wideentry-element-for-widecontrol-format.md) que muestran objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="661e7-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="661e7-149">El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) especifica los datos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="661e7-150">A diferencia de otros tipos de vistas, un control ancho solo puede mostrar un elemento.</span><span class="sxs-lookup"><span data-stu-id="661e7-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="661e7-151">El elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) especifica la propiedad cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="661e7-152">Debe especificar una propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="661e7-153">El elemento [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) especifica el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="661e7-154">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="661e7-155">El elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) especifica un patrón que se usa para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="661e7-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="661e7-156">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-156">This element is optional.</span></span>

<span data-ttu-id="661e7-157">Para obtener un ejemplo de un archivo de formato completo que define una definición de vista ancha, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="661e7-158">Definir los objetos que usan la vista amplia</span><span class="sxs-lookup"><span data-stu-id="661e7-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="661e7-159">Hay dos maneras de definir qué objetos .NET usan la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="661e7-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="661e7-160">Puede usar el elemento [ViewSelectedBy](./viewselectedby-element-format.md) para definir los objetos que se pueden mostrar en todas las definiciones de la vista, o puede usar el elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) para definir qué objetos se muestran en una definición específica de la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="661e7-161">En la mayoría de los casos, una vista solo tiene una definición, por lo que los objetos se definen normalmente mediante el elemento [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="661e7-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="661e7-162">En el ejemplo siguiente se muestra cómo definir los objetos que se muestran en la vista amplia mediante los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="661e7-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="661e7-163">No hay ningún límite en el número de elementos [TypeName](./typename-element-for-viewselectedby-format.md) que se pueden especificar y su orden no es significativo.</span><span class="sxs-lookup"><span data-stu-id="661e7-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="661e7-164">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="661e7-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="661e7-165">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="661e7-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="661e7-166">El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el .net que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="661e7-167">El nombre completo del tipo .NET es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="661e7-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="661e7-168">Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="661e7-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="661e7-169">Para obtener un ejemplo de un archivo de formato completo, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="661e7-170">En el ejemplo siguiente se usan los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="661e7-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="661e7-171">Use conjuntos de selección en los que tenga un conjunto relacionado de objetos que se muestran mediante varias vistas, como cuando se define una vista amplia y una vista de tabla para los mismos objetos.</span><span class="sxs-lookup"><span data-stu-id="661e7-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="661e7-172">Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="661e7-173">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="661e7-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="661e7-174">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="661e7-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="661e7-175">El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos que se pueden mostrar en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="661e7-176">Debe especificar al menos un conjunto o tipo de selección para la vista, pero no se puede especificar un número máximo de elementos.</span><span class="sxs-lookup"><span data-stu-id="661e7-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="661e7-177">En el ejemplo siguiente se muestra cómo definir los objetos mostrados por una definición específica de la vista ampliada mediante el elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) .</span><span class="sxs-lookup"><span data-stu-id="661e7-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="661e7-178">Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que especifica cuándo se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="661e7-179">Para obtener más información sobre cómo crear condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="661e7-180">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en una definición específica de la vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="661e7-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="661e7-181">El elemento [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) define qué objetos se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="661e7-182">El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el .net que se muestra en la definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="661e7-183">Cuando se usa este elemento, se requiere el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="661e7-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="661e7-184">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="661e7-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="661e7-185">El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (no se muestra) especifica un conjunto de objetos que se pueden mostrar en esta definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="661e7-186">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="661e7-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="661e7-187">El elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (no se muestra) especifica una condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="661e7-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="661e7-188">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="661e7-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="661e7-189">Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="661e7-190">Mostrar grupos de objetos en una vista amplia</span><span class="sxs-lookup"><span data-stu-id="661e7-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="661e7-191">Puede separar los objetos que se muestran en la vista amplia en grupos.</span><span class="sxs-lookup"><span data-stu-id="661e7-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="661e7-192">Esto no significa que defina un grupo, solo que Windows PowerShell inicie un nuevo grupo siempre que cambie el valor de una propiedad o un script específicos.</span><span class="sxs-lookup"><span data-stu-id="661e7-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="661e7-193">En el ejemplo siguiente, se inicia un nuevo grupo siempre que cambia el valor de la propiedad [System. ServiceProcess. ServiceController. serviceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) .</span><span class="sxs-lookup"><span data-stu-id="661e7-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="661e7-194">Los siguientes elementos XML se utilizan para definir cuándo se inicia un grupo:</span><span class="sxs-lookup"><span data-stu-id="661e7-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="661e7-195">El elemento [GroupBy](./groupby-element-for-view-format.md) define la propiedad o el script que inicia el nuevo grupo y define cómo se muestra el grupo.</span><span class="sxs-lookup"><span data-stu-id="661e7-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="661e7-196">El elemento [PropertyName](./propertyname-element-for-groupby-format.md) especifica la propiedad que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="661e7-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="661e7-197">Debe especificar una propiedad o un script para iniciar el grupo, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="661e7-198">El elemento [ScriptBlock](./scriptblock-element-for-groupby-format.md) especifica el script que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="661e7-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="661e7-199">Debe especificar un script o una propiedad para iniciar el grupo, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="661e7-200">El elemento [Label](./label-element-for-groupby-format.md) define una etiqueta que se muestra al principio de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="661e7-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="661e7-201">Además del texto especificado por este elemento, Windows PowerShell muestra el valor que desencadenó el nuevo grupo y agrega una línea en blanco antes y después de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="661e7-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="661e7-202">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-202">This element is optional.</span></span>

- <span data-ttu-id="661e7-203">El elemento [CustomControl](./customcontrol-element-for-groupby-format.md) define un control que se utiliza para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="661e7-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="661e7-204">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-204">This element is optional.</span></span>

- <span data-ttu-id="661e7-205">El elemento [CustomControlName](./customcontrolname-element-for-groupby-format.md) especifica un control común o de vista que se usa para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="661e7-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="661e7-206">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="661e7-206">This element is optional.</span></span>

<span data-ttu-id="661e7-207">Para obtener un ejemplo de un archivo de formato completo que define grupos, vea [vista ampliada (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="661e7-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="661e7-208">Usar cadenas de formato</span><span class="sxs-lookup"><span data-stu-id="661e7-208">Using Format Strings</span></span>

<span data-ttu-id="661e7-209">Las cadenas de formato se pueden agregar a una vista amplia para definir mejor cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="661e7-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="661e7-210">En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="661e7-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="661e7-211">Los siguientes elementos XML se pueden usar para especificar un modelo de formato:</span><span class="sxs-lookup"><span data-stu-id="661e7-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="661e7-212">El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) especifica los datos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="661e7-213">El elemento [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) especifica la propiedad cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="661e7-214">Debe especificar una propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="661e7-215">El elemento [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="661e7-216">El elemento [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="661e7-217">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="661e7-218">En el ejemplo siguiente, se llama al método `ToString` para dar formato al valor del script.</span><span class="sxs-lookup"><span data-stu-id="661e7-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="661e7-219">Los scripts pueden llamar a cualquier método de un objeto.</span><span class="sxs-lookup"><span data-stu-id="661e7-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="661e7-220">Por consiguiente, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida del script.</span><span class="sxs-lookup"><span data-stu-id="661e7-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="661e7-221">El siguiente elemento XML se puede usar para llamar al método `ToString`:</span><span class="sxs-lookup"><span data-stu-id="661e7-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="661e7-222">El elemento [WideItem](./wideitem-element-for-widecontrol-format.md) especifica los datos que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="661e7-223">El elemento [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (no se muestra) especifica el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="661e7-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="661e7-224">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="661e7-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="661e7-225">Véase también</span><span class="sxs-lookup"><span data-stu-id="661e7-225">See Also</span></span>

[<span data-ttu-id="661e7-226">Vista amplia (básica)</span><span class="sxs-lookup"><span data-stu-id="661e7-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="661e7-227">Vista amplia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="661e7-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="661e7-228">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="661e7-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
