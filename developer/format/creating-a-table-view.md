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
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861501"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="196b1-102">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="196b1-102">Creating a Table View</span></span>

<span data-ttu-id="196b1-103">Una vista de tabla muestra los datos en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="196b1-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="196b1-104">Cada fila de la tabla representa un objeto. NET, y cada columna de la tabla representa una propiedad del objeto o un valor de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="196b1-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="196b1-105">Puede definir una vista de tabla que muestra todas las propiedades de un objeto o un subconjunto de las propiedades de un objeto.</span><span class="sxs-lookup"><span data-stu-id="196b1-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="196b1-106">Una presentación de la vista de tabla</span><span class="sxs-lookup"><span data-stu-id="196b1-106">A Table View Display</span></span>

<span data-ttu-id="196b1-107">El ejemplo siguiente muestra cómo Windows PowerShell muestra el [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto devuelto por la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="196b1-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="196b1-108">Para este objeto, Windows PowerShell ha definido una vista de tabla que muestra la `Status` propiedad, el `Name` propiedad (esta propiedad es una propiedad de alias para el `ServiceName` propiedad) y el `DisplayName` propiedad.</span><span class="sxs-lookup"><span data-stu-id="196b1-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="196b1-109">Cada fila de la tabla representa un objeto devuelto por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="196b1-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="196b1-110">Define la vista de tabla</span><span class="sxs-lookup"><span data-stu-id="196b1-110">Defining the Table View</span></span>

<span data-ttu-id="196b1-111">¿El siguiente XML muestra el esquema de vista de tabla para mostrar el [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="196b1-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="196b1-112">Debe especificar cada propiedad que desea que aparezca en la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="196b1-113">Los siguientes elementos XML se usan para definir una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="196b1-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="196b1-114">El [vista](./view-element-format.md) elemento es el elemento primario de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="196b1-115">(Esto es el mismo elemento primario de la lista, las vistas de control ancho y personalizadas).</span><span class="sxs-lookup"><span data-stu-id="196b1-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="196b1-116">El [nombre](./name-element-for-view-format.md) elemento especifica el nombre de la vista.</span><span class="sxs-lookup"><span data-stu-id="196b1-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="196b1-117">Este elemento es necesario para todas las vistas.</span><span class="sxs-lookup"><span data-stu-id="196b1-117">This element is required for all views.</span></span>

- <span data-ttu-id="196b1-118">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="196b1-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="196b1-119">Este elemento es necesario.</span><span class="sxs-lookup"><span data-stu-id="196b1-119">This element is required.</span></span>

- <span data-ttu-id="196b1-120">El [GroupBy](./groupby-element-for-view-format.md) elemento (no se muestra en este ejemplo) define cuando se muestre un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="196b1-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="196b1-121">Cada vez que cambia el valor de una propiedad específica o un script, se inicia un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="196b1-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="196b1-122">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-122">This element is optional.</span></span>

- <span data-ttu-id="196b1-123">El [controles](./controls-element-for-view-format.md) elemento (no se muestra en este ejemplo) define los controles personalizados que se definen mediante la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="196b1-124">Los controles ofrecen una manera de especificar cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="196b1-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="196b1-125">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-125">This element is optional.</span></span> <span data-ttu-id="196b1-126">Una vista puede definir sus propios controles personalizados, o puede usar controles comunes que pueden usarse en cualquier vista en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="196b1-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="196b1-127">Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="196b1-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="196b1-128">El [HideTableHeaders](./hidetableheaders-element-format.md) elemento (no aparece en este ejemplo) especifica que la tabla no mostrará ninguna etiqueta en la parte superior de la tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="196b1-129">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-129">This element is optional.</span></span>

- <span data-ttu-id="196b1-130">El [TableControl](./tablecontrol-element-format.md) elemento que define la información de encabezado y fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="196b1-131">Al igual que todas las demás vistas, una vista de tabla puede mostrar los valores de las propiedades del objeto o los valores generados por las secuencias de comandos.</span><span class="sxs-lookup"><span data-stu-id="196b1-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="196b1-132">Definir los encabezados de columna</span><span class="sxs-lookup"><span data-stu-id="196b1-132">Defining Column Headers</span></span>

1. <span data-ttu-id="196b1-133">El [TableHeaders](./tableheaders-element-format.md) elemento y sus elementos secundarios definen lo que se muestra en la parte superior de la tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="196b1-134">El [TableColumnHeader](./tablecolumnheader-element-format.md) elemento define lo que se muestra en la parte superior de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="196b1-135">Estos elementos se especifican en el orden en que desea que los encabezados se muestran.</span><span class="sxs-lookup"><span data-stu-id="196b1-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="196b1-136">No hay ningún límite en el número de estos elementos que puede usar, pero el número de [TableColumnHeader](./tablecolumnheader-element-format.md) elementos en la vista de tabla deben ser igual al número de [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elementos que se usan.</span><span class="sxs-lookup"><span data-stu-id="196b1-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="196b1-137">El [etiqueta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento especifica el texto que se muestra.</span><span class="sxs-lookup"><span data-stu-id="196b1-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="196b1-138">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-138">This element is optional.</span></span>

4. <span data-ttu-id="196b1-139">El [ancho](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento especifica el ancho (en caracteres) de la columna.</span><span class="sxs-lookup"><span data-stu-id="196b1-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="196b1-140">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-140">This element is optional.</span></span>

5. <span data-ttu-id="196b1-141">El [alineación](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento especifica cómo se muestra la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="196b1-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="196b1-142">La etiqueta se alinea a la izquierda, a la derecha, o centrada.</span><span class="sxs-lookup"><span data-stu-id="196b1-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="196b1-143">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="196b1-144">Definir las filas de tabla</span><span class="sxs-lookup"><span data-stu-id="196b1-144">Defining the Table Rows</span></span>

<span data-ttu-id="196b1-145">Vistas de tabla pueden proporcionar una o varias definiciones que especifican qué datos se muestran en las filas de la tabla mediante el uso de los elementos secundarios de la [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="196b1-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="196b1-146">Tenga en cuenta que puede especificar varias definiciones para las filas de la tabla, pero los encabezados de las filas sigue siendo el mismo, independientemente de qué definición de fila se utiliza.</span><span class="sxs-lookup"><span data-stu-id="196b1-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="196b1-147">Por lo general, una tabla tiene una única definición.</span><span class="sxs-lookup"><span data-stu-id="196b1-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="196b1-148">¿En el ejemplo siguiente, la vista proporciona una única definición que muestra los valores de varias propiedades de la [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="196b1-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="196b1-149">Una vista de tabla puede mostrar el valor de una propiedad o el valor de una secuencia de comandos (no se muestra en el ejemplo) en sus filas.</span><span class="sxs-lookup"><span data-stu-id="196b1-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="196b1-150">Los siguientes elementos XML pueden usarse para proporcionar las definiciones para una fila:</span><span class="sxs-lookup"><span data-stu-id="196b1-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="196b1-151">El [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento y sus elementos secundarios definen lo que se muestra en las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="196b1-152">El [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento proporciona una definición de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="196b1-153">Al menos un [TableRowEntry](./listentry-element-for-listcontrol-format.md) es necesario; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="196b1-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="196b1-154">En la mayoría de los casos, una vista tendrá una única definición.</span><span class="sxs-lookup"><span data-stu-id="196b1-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="196b1-155">El [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento especifica los objetos que se muestran en una definición específica.</span><span class="sxs-lookup"><span data-stu-id="196b1-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="196b1-156">Este elemento es opcional y solo es necesario cuando definir varios [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementos que muestran los distintos objetos.</span><span class="sxs-lookup"><span data-stu-id="196b1-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="196b1-157">El [ajustar](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) elemento especifica que el texto que supera el ancho de columna se muestra en la línea siguiente.</span><span class="sxs-lookup"><span data-stu-id="196b1-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="196b1-158">De forma predeterminada, el texto que supera el ancho de columna se trunca.</span><span class="sxs-lookup"><span data-stu-id="196b1-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="196b1-159">El [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento define las propiedades o scripts cuyos valores se muestran en la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="196b1-160">El [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="196b1-161">Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento es necesario para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="196b1-162">La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="196b1-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="196b1-163">El [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="196b1-164">Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="196b1-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="196b1-165">El [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="196b1-166">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="196b1-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="196b1-167">El [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="196b1-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="196b1-168">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-168">This element is optional.</span></span>

- <span data-ttu-id="196b1-169">El [alineación](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica cómo se muestra el valor de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="196b1-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="196b1-170">El valor puede ser alineado a la izquierda, a la derecha, o centrado.</span><span class="sxs-lookup"><span data-stu-id="196b1-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="196b1-171">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="196b1-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="196b1-172">Definir los objetos que utilizan la vista de tabla</span><span class="sxs-lookup"><span data-stu-id="196b1-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="196b1-173">Hay dos maneras de definir qué objetos de .NET utilizan la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="196b1-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="196b1-174">Puede usar el [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir los objetos que se pueden mostrar todas las definiciones de la vista, o bien puede usar el [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir qué objetos se muestran mediante un definición específica de la vista.</span><span class="sxs-lookup"><span data-stu-id="196b1-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="196b1-175">En la mayoría de los casos, una vista tiene una única definición, por lo que normalmente se definen los objetos mediante el [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="196b1-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="196b1-176">El ejemplo siguiente muestra cómo se definen los objetos que se muestran en la vista de tabla mediante el [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="196b1-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="196b1-177">No hay ningún límite al número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que puede especificar y su orden no es significativo.</span><span class="sxs-lookup"><span data-stu-id="196b1-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="196b1-178">Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de tabla:</span><span class="sxs-lookup"><span data-stu-id="196b1-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="196b1-179">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="196b1-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="196b1-180">El [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica el objeto .NET que se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="196b1-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="196b1-181">Se requiere el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="196b1-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="196b1-182">Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="196b1-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="196b1-183">En el ejemplo siguiente se usa el [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="196b1-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="196b1-184">Usar conjuntos de selección donde haya un conjunto de objetos que se muestran usando varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="196b1-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="196b1-185">Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="196b1-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="196b1-186">Los siguientes elementos XML pueden usarse para especificar los objetos utilizados por la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="196b1-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="196b1-187">El [ViewSelectedBy](./viewselectedby-element-format.md) elemento define los objetos que se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="196b1-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="196b1-188">El [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento especifica un conjunto de objetos que se puede mostrar la vista.</span><span class="sxs-lookup"><span data-stu-id="196b1-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="196b1-189">Debe especificar al menos un conjunto de selección o tipo de la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="196b1-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="196b1-190">El ejemplo siguiente muestra cómo definir los objetos mostrados por una definición específica de la vista de tabla mediante el [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="196b1-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="196b1-191">Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que se especifica cuando se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="196b1-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="196b1-192">Para obtener más información acerca de cómo crear una selección de las condiciones, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="196b1-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="196b1-193">Al crear varias definiciones de la vista de tabla no se puede especificar encabezados de columna diferente.</span><span class="sxs-lookup"><span data-stu-id="196b1-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="196b1-194">Puede especificar sólo lo que se muestra en las filas de la tabla, como los objetos que se muestran.</span><span class="sxs-lookup"><span data-stu-id="196b1-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="196b1-195">Los siguientes elementos XML pueden usarse para especificar los objetos usados por una definición específica de la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="196b1-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="196b1-196">El [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento define los objetos que se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="196b1-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="196b1-197">El [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento especifica el objeto .NET que se muestra la definición.</span><span class="sxs-lookup"><span data-stu-id="196b1-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="196b1-198">Cuando se usa este elemento, se requiere el nombre de tipo .NET completo.</span><span class="sxs-lookup"><span data-stu-id="196b1-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="196b1-199">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="196b1-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="196b1-200">El [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica un conjunto de objetos que se pueden mostrar por esta definición.</span><span class="sxs-lookup"><span data-stu-id="196b1-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="196b1-201">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="196b1-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="196b1-202">El [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (no mostrado) especifica una condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="196b1-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="196b1-203">Debe especificar al menos un tipo, el conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="196b1-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="196b1-204">Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="196b1-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="196b1-205">Usar cadenas de formato</span><span class="sxs-lookup"><span data-stu-id="196b1-205">Using Format Strings</span></span>

<span data-ttu-id="196b1-206">Las cadenas de formato se pueden agregar a una vista para definir cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="196b1-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="196b1-207">El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.</span><span class="sxs-lookup"><span data-stu-id="196b1-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="196b1-208">Los siguientes elementos XML pueden usarse para especificar un patrón de formato:</span><span class="sxs-lookup"><span data-stu-id="196b1-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="196b1-209">El [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="196b1-210">Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento es necesario para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="196b1-211">La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="196b1-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="196b1-212">El [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la propiedad cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="196b1-213">Debe especificar una propiedad o una secuencia de comandos, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="196b1-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="196b1-214">El [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="196b1-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="196b1-215">En el ejemplo siguiente, la `ToString` método se llama para dar formato al valor de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="196b1-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="196b1-216">Las secuencias de comandos pueden llamar a cualquier método de un objeto.</span><span class="sxs-lookup"><span data-stu-id="196b1-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="196b1-217">Por lo tanto, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="196b1-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="196b1-218">El siguiente elemento XML puede usarse para llamar a la `ToString` método:</span><span class="sxs-lookup"><span data-stu-id="196b1-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="196b1-219">El [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="196b1-220">Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento es necesario para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="196b1-221">La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="196b1-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="196b1-222">El [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento especifica la secuencia de comandos cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="196b1-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="196b1-223">Debe especificar un script o una propiedad, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="196b1-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="196b1-224">Véase también</span><span class="sxs-lookup"><span data-stu-id="196b1-224">See Also</span></span>

[<span data-ttu-id="196b1-225">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="196b1-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
