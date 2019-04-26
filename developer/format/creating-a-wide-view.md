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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066726"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="b5ff3-102">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="b5ff3-102">Creating a Wide View</span></span>

<span data-ttu-id="b5ff3-103">Una vista amplia muestra un valor único para cada objeto que se muestra.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="b5ff3-104">El valor de una propiedad de objeto .NET o el valor de una secuencia de comandos, puede ser el valor mostrado.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="b5ff3-105">De forma predeterminada, no hay ninguna etiqueta ni el encabezado para esta vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="b5ff3-106">Una presentación de la vista ampliada</span><span class="sxs-lookup"><span data-stu-id="b5ff3-106">A Wide View Display</span></span>

<span data-ttu-id="b5ff3-107">El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto devuelto por la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet cuando su salida se canaliza hacia el [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="b5ff3-108">(De forma predeterminada, el [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devuelve una vista de tabla.) En este ejemplo, las dos columnas se utilizan para mostrar el nombre del proceso para cada objeto devuelto.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="b5ff3-109">No se muestra el nombre de la propiedad del objeto, solo el valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="b5ff3-110">Define la vista ancha</span><span class="sxs-lookup"><span data-stu-id="b5ff3-110">Defining the Wide View</span></span>

<span data-ttu-id="b5ff3-111">El siguiente XML muestra el esquema de la vista ampliada para la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="b5ff3-112">Los siguientes elementos XML se usan para definir una vista amplia:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="b5ff3-113">El [vista](./view-element-format.md) elemento es el elemento primario de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="b5ff3-114">(Esto es el mismo elemento primario para la tabla, lista y vistas de control personalizado).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="b5ff3-115">El [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="b5ff3-116">Este elemento es necesario para todas las vistas.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-116">This element is required for all views.</span></span>

- <span data-ttu-id="b5ff3-117">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="b5ff3-118">Este elemento es necesario.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-118">This element is required.</span></span>

- <span data-ttu-id="b5ff3-119">El [GroupBy](./groupby-element-for-view-format.md) elemento define cuando se muestre un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="b5ff3-120">Cada vez que cambia el valor de una propiedad específica o un script, se inicia un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b5ff3-121">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-121">This element is optional.</span></span>

- <span data-ttu-id="b5ff3-122">El [controles](./controls-element-for-view-format.md) elementos define los controles personalizados que se definen mediante la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="b5ff3-123">Los controles ofrecen una manera de especificar cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="b5ff3-124">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-124">This element is optional.</span></span> <span data-ttu-id="b5ff3-125">Una vista puede definir sus propios controles personalizados, o puede usar controles comunes que pueden usarse en cualquier vista en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="b5ff3-126">Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="b5ff3-127">El [WideControl](./widecontrol-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="b5ff3-128">En el ejemplo anterior, la vista está diseñada para mostrar el [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propiedad.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="b5ff3-129">Para obtener un ejemplo de un archivo de formato completo que define una vista amplia simple, vea [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="b5ff3-130">Proporcionar las definiciones para la vista ampliada</span><span class="sxs-lookup"><span data-stu-id="b5ff3-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="b5ff3-131">Vista amplia puede proporcionar una o varias definiciones mediante el uso de los elementos secundarios de la [WideControl](./widecontrol-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="b5ff3-132">Normalmente, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="b5ff3-133">En el ejemplo siguiente, la vista proporciona una única definición que muestra el valor de la [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propiedad.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="b5ff3-134">El valor de una propiedad o el valor de una secuencia de comandos (no se muestra en el ejemplo), puede mostrar una vista amplia.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="b5ff3-135">Los siguientes elementos XML pueden usarse para proporcionar las definiciones para una vista amplia:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="b5ff3-136">El [WideControl](./widecontrol-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="b5ff3-137">El [AutoSize](./autosize-element-for-widecontrol-format.md) elemento especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="b5ff3-138">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-138">This element is optional.</span></span>

- <span data-ttu-id="b5ff3-139">El [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento especifica el número de columnas mostradas en la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="b5ff3-140">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-140">This element is optional.</span></span>

- <span data-ttu-id="b5ff3-141">El [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento proporciona las definiciones de la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="b5ff3-142">En la mayoría de los casos, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="b5ff3-143">Este elemento es necesario.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-143">This element is required.</span></span>

- <span data-ttu-id="b5ff3-144">El [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento proporciona una definición de la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="b5ff3-145">Al menos un [WideEntry](./wideentry-element-for-widecontrol-format.md) es necesario; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="b5ff3-146">En la mayoría de los casos, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="b5ff3-147">El [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento especifica los objetos que se muestran en una definición específica.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="b5ff3-148">Este elemento es opcional y solo es necesario cuando definir varios [WideEntry](./wideentry-element-for-widecontrol-format.md) elementos que muestran los distintos objetos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="b5ff3-149">El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento especifica los datos que se muestran la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="b5ff3-150">A diferencia de otros tipos de vistas, un gran control puede mostrar un único elemento.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="b5ff3-151">El [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="b5ff3-152">Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b5ff3-153">El [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b5ff3-154">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="b5ff3-155">El [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento especifica un patrón que se usa para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="b5ff3-156">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-156">This element is optional.</span></span>

<span data-ttu-id="b5ff3-157">Para obtener un ejemplo de un archivo de formato completo que define una definición de vista ampliada, vea [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="b5ff3-158">Definir los objetos que utilizan la vista ampliada</span><span class="sxs-lookup"><span data-stu-id="b5ff3-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="b5ff3-159">Hay dos maneras de definir qué objetos de .NET usan la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="b5ff3-160">Puede usar el [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir los objetos que se pueden mostrar todas las definiciones de la vista, o bien puede usar el [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento para definir qué objetos se muestran mediante un definición específica de la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="b5ff3-161">En la mayoría de los casos, una vista tiene una única definición, por lo que normalmente se definen los objetos mediante el [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="b5ff3-162">El ejemplo siguiente muestra cómo se definen los objetos que se muestran utilizando la vista amplia el [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b5ff3-163">No hay ningún límite al número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que puede especificar y su orden no es significativo.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="b5ff3-164">Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="b5ff3-165">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="b5ff3-166">El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica .NET que se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="b5ff3-167">Se requiere el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="b5ff3-168">Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b5ff3-169">Para obtener un ejemplo de un archivo de formato completo, vea [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="b5ff3-170">En el ejemplo siguiente se usa el [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b5ff3-171">Usar conjuntos de selección donde haya un conjunto de objetos que se muestran usando varias vistas, como cuando se define una vista amplia y una vista de tabla para los mismos objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="b5ff3-172">Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="b5ff3-173">Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="b5ff3-174">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="b5ff3-175">El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento especifica un conjunto de objetos que se puede mostrar la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="b5ff3-176">Debe especificar al menos un conjunto de selección o tipo de la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b5ff3-177">El ejemplo siguiente muestra cómo definir los objetos mostrados por una definición específica de la vista ampliada mediante el [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="b5ff3-178">Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que se especifica cuando se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="b5ff3-179">Para obtener más información acerca de cómo crear una selección de las condiciones, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="b5ff3-180">Los siguientes elementos XML pueden usarse para especificar los objetos usados por una definición específica de la vista ampliada:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="b5ff3-181">El [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento define los objetos que se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="b5ff3-182">El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica .NET que se muestra la definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="b5ff3-183">Cuando se usa este elemento es necesario el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="b5ff3-184">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b5ff3-185">El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (no mostrado) especifica un conjunto de objetos que se pueden mostrar por esta definición.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="b5ff3-186">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b5ff3-187">El [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) elemento (no mostrado) especifica una condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b5ff3-188">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="b5ff3-189">Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="b5ff3-190">Muestra los grupos de objetos en una vista amplia</span><span class="sxs-lookup"><span data-stu-id="b5ff3-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="b5ff3-191">Puede separar los objetos que se muestran en la vista ampliada en grupos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="b5ff3-192">Esto no significa que definir un grupo, solo que PowerShell de Windows se inicia un nuevo grupo cada vez que cambia el valor de una propiedad específica o un script.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b5ff3-193">En el ejemplo siguiente, se inicia un nuevo grupo cada vez que el valor de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) los cambios de propiedad.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="b5ff3-194">Los siguientes elementos XML se usan para definir cuando se inicia un grupo:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="b5ff3-195">El [GroupBy](./groupby-element-for-view-format.md) elemento define la propiedad o el script que se inicia el nuevo grupo y define cómo se muestra el grupo.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="b5ff3-196">El [PropertyName](./propertyname-element-for-groupby-format.md) elemento especifica la propiedad que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="b5ff3-197">Debe especificar una propiedad o un script para iniciar el grupo, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="b5ff3-198">El [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="b5ff3-199">Debe especificar un script o una propiedad para iniciar el grupo, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="b5ff3-200">El [etiqueta](./label-element-for-groupby-format.md) elemento define una etiqueta que se muestra al principio de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="b5ff3-201">Además del texto especificado por este elemento, Windows PowerShell muestra el valor que desencadena el nuevo grupo y agrega una línea en blanco antes y después de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="b5ff3-202">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-202">This element is optional.</span></span>

- <span data-ttu-id="b5ff3-203">El [control personalizado](./customcontrol-element-for-groupby-format.md) elemento define un control que se usa para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="b5ff3-204">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-204">This element is optional.</span></span>

- <span data-ttu-id="b5ff3-205">El [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento especifica un común o control que se usa para mostrar los datos de vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="b5ff3-206">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-206">This element is optional.</span></span>

<span data-ttu-id="b5ff3-207">Para obtener un ejemplo de un archivo de formato completo que define los grupos, consulte [vista amplia (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="b5ff3-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="b5ff3-208">Usar cadenas de formato</span><span class="sxs-lookup"><span data-stu-id="b5ff3-208">Using Format Strings</span></span>

<span data-ttu-id="b5ff3-209">Las cadenas de formato se pueden agregar a una vista amplia para definir cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="b5ff3-210">El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="b5ff3-211">Los siguientes elementos XML pueden usarse para especificar un patrón de formato:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="b5ff3-212">El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento especifica los datos que se muestran la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="b5ff3-213">El [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="b5ff3-214">Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b5ff3-215">El [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista</span><span class="sxs-lookup"><span data-stu-id="b5ff3-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="b5ff3-216">El [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b5ff3-217">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="b5ff3-218">En el ejemplo siguiente, la `ToString` método se llama para dar formato al valor de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="b5ff3-219">Las secuencias de comandos pueden llamar a cualquier método de un objeto.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="b5ff3-220">Por lo tanto, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="b5ff3-221">El siguiente elemento XML puede usarse para llamar a la `ToString` método:</span><span class="sxs-lookup"><span data-stu-id="b5ff3-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="b5ff3-222">El [WideItem](./wideitem-element-for-widecontrol-format.md) elemento especifica los datos que se muestran la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="b5ff3-223">El [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (no mostrado) especifica la secuencia de comandos cuyo valor se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="b5ff3-224">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5ff3-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5ff3-225">Véase también</span><span class="sxs-lookup"><span data-stu-id="b5ff3-225">See Also</span></span>

[<span data-ttu-id="b5ff3-226">Vista amplia (Basic)</span><span class="sxs-lookup"><span data-stu-id="b5ff3-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="b5ff3-227">Vista amplia (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="b5ff3-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="b5ff3-228">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5ff3-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
