---
title: Crear una vista de tabla | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363414"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="7bbd7-102">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="7bbd7-102">Creating a Table View</span></span>

<span data-ttu-id="7bbd7-103">Una vista de tabla muestra los datos en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="7bbd7-104">Cada fila de la tabla representa un objeto .NET y cada columna de la tabla representa una propiedad del objeto o un valor de script.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="7bbd7-105">Puede definir una vista de tabla que muestre todas las propiedades de un objeto o un subconjunto de las propiedades de un objeto.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="7bbd7-106">Visualización de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="7bbd7-106">A Table View Display</span></span>

<span data-ttu-id="7bbd7-107">En el ejemplo siguiente se muestra cómo Windows PowerShell muestra el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) devuelto por el cmdlet [Get-Service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="7bbd7-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="7bbd7-108">Para este objeto, Windows PowerShell ha definido una vista de tabla que muestra la propiedad `Status`, la propiedad `Name` (esta propiedad es una propiedad de alias para la propiedad `ServiceName`) y la propiedad `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="7bbd7-109">Cada fila de la tabla representa un objeto devuelto por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="7bbd7-110">Definir la vista de tabla</span><span class="sxs-lookup"><span data-stu-id="7bbd7-110">Defining the Table View</span></span>

<span data-ttu-id="7bbd7-111">El siguiente XML muestra el esquema de la vista de tabla para mostrar [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) (objeto).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="7bbd7-112">Debe especificar cada propiedad que desea que se muestre en la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="7bbd7-113">Los siguientes elementos XML se utilizan para definir una vista de lista:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="7bbd7-114">El elemento de [vista](./view-element-format.md) es el elemento primario de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="7bbd7-115">(Es el mismo elemento primario para las vistas de lista, ancho y control personalizado).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="7bbd7-116">El elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="7bbd7-117">Este elemento es necesario para todas las vistas.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-117">This element is required for all views.</span></span>

- <span data-ttu-id="7bbd7-118">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="7bbd7-119">Se requiere el elemento.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-119">This element is required.</span></span>

- <span data-ttu-id="7bbd7-120">El elemento [GroupBy](./groupby-element-for-view-format.md) (no se muestra en este ejemplo) define cuándo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="7bbd7-121">Se inicia un nuevo grupo siempre que cambia el valor de una propiedad o un script específicos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="7bbd7-122">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-122">This element is optional.</span></span>

- <span data-ttu-id="7bbd7-123">El elemento [Controls](./controls-element-for-view-format.md) (no se muestra en este ejemplo) define los controles personalizados que se definen en la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="7bbd7-124">Los controles ofrecen una manera de especificar mejor cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="7bbd7-125">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-125">This element is optional.</span></span> <span data-ttu-id="7bbd7-126">Una vista puede definir sus propios controles personalizados o puede usar controles comunes que se pueden usar en cualquier vista del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="7bbd7-127">Para obtener más información sobre los controles personalizados, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="7bbd7-128">El elemento [HideTableHeaders](./hidetableheaders-element-format.md) (no se muestra en este ejemplo) especifica que la tabla no mostrará ninguna etiqueta en la parte superior de la tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="7bbd7-129">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-129">This element is optional.</span></span>

- <span data-ttu-id="7bbd7-130">El elemento [tablecontrol (](./tablecontrol-element-format.md) que define la información de encabezado y fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="7bbd7-131">Al igual que todas las demás vistas, una vista de tabla puede mostrar los valores de las propiedades de objeto o de los valores generados por scripts.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="7bbd7-132">Definir encabezados de columna</span><span class="sxs-lookup"><span data-stu-id="7bbd7-132">Defining Column Headers</span></span>

1. <span data-ttu-id="7bbd7-133">El elemento [TableHeaders](./tableheaders-element-format.md) y sus elementos secundarios definen lo que se muestra en la parte superior de la tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="7bbd7-134">El elemento [TableColumnHeader](./tablecolumnheader-element-format.md) define lo que se muestra en la parte superior de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="7bbd7-135">Especifique estos elementos en el orden en que desea que se muestren los encabezados.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="7bbd7-136">No hay ningún límite en cuanto al número de estos elementos que puede utilizar, pero el número de elementos [TableColumnHeader](./tablecolumnheader-element-format.md) en la vista de tabla debe ser igual al número de elementos [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) que use.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="7bbd7-137">El elemento [etiqueta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) especifica el texto que se muestra.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="7bbd7-138">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-138">This element is optional.</span></span>

4. <span data-ttu-id="7bbd7-139">El elemento [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) especifica el ancho (en caracteres) de la columna.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="7bbd7-140">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-140">This element is optional.</span></span>

5. <span data-ttu-id="7bbd7-141">El elemento [alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) especifica cómo se muestra la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="7bbd7-142">La etiqueta se puede alinear a la izquierda, a la derecha o centrada.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="7bbd7-143">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="7bbd7-144">Definir las filas de la tabla</span><span class="sxs-lookup"><span data-stu-id="7bbd7-144">Defining the Table Rows</span></span>

<span data-ttu-id="7bbd7-145">Las vistas de tabla pueden proporcionar una o más definiciones que especifican qué datos se muestran en las filas de la tabla mediante los elementos secundarios del elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7bbd7-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="7bbd7-146">Tenga en cuenta que puede especificar varias definiciones para las filas de la tabla, pero los encabezados de las filas siguen siendo los mismos, independientemente de la definición de fila que se utilice.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="7bbd7-147">Normalmente, una tabla solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="7bbd7-148">En el ejemplo siguiente, la vista proporciona una única definición que muestra los valores de varias propiedades de [System. Diagnostics. Process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) (objeto).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="7bbd7-149">Una vista de tabla puede mostrar el valor de una propiedad o el valor de un script (no se muestra en el ejemplo) en sus filas.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="7bbd7-150">Los siguientes elementos XML se pueden usar para proporcionar definiciones para una fila:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="7bbd7-151">El elemento [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) y sus elementos secundarios definen lo que se muestra en las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="7bbd7-152">El elemento [TableRowEntry](./listentry-element-for-listcontrol-format.md) proporciona una definición de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="7bbd7-153">Se requiere al menos un [TableRowEntry](./listentry-element-for-listcontrol-format.md) ; sin embargo, no hay ningún límite máximo para el número de elementos que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="7bbd7-154">En la mayoría de los casos, una vista solo tendrá una definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="7bbd7-155">El elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) especifica los objetos que se muestran en una definición específica.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="7bbd7-156">Este elemento es opcional y solo es necesario cuando se definen varios elementos [TableRowEntry](./listentry-element-for-listcontrol-format.md) que muestran objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="7bbd7-157">El elemento [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) especifica que el texto que supera el ancho de columna se muestra en la línea siguiente.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="7bbd7-158">De forma predeterminada, el texto que supera el ancho de columna se trunca.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="7bbd7-159">El elemento [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) define las propiedades o los scripts cuyos valores se muestran en la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="7bbd7-160">El elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="7bbd7-161">Se requiere un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="7bbd7-162">La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="7bbd7-163">El elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica la propiedad cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="7bbd7-164">Debe especificar una propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="7bbd7-165">El elemento [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica el script cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="7bbd7-166">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="7bbd7-167">El elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="7bbd7-168">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-168">This element is optional.</span></span>

- <span data-ttu-id="7bbd7-169">El elemento [alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica cómo se muestra el valor de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="7bbd7-170">El valor se puede alinear a la izquierda, a la derecha o al centro.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="7bbd7-171">Este elemento es opcional.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="7bbd7-172">Definir los objetos que utilizan la vista de tabla</span><span class="sxs-lookup"><span data-stu-id="7bbd7-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="7bbd7-173">Hay dos maneras de definir qué objetos .NET usan la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="7bbd7-174">Puede usar el elemento [ViewSelectedBy](./viewselectedby-element-format.md) para definir los objetos que se pueden mostrar en todas las definiciones de la vista, o puede usar el elemento [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) para definir qué objetos se muestran en una definición específica de la vista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="7bbd7-175">En la mayoría de los casos, una vista solo tiene una definición, por lo que los objetos se definen normalmente mediante el elemento [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7bbd7-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="7bbd7-176">En el ejemplo siguiente se muestra cómo definir los objetos que se muestran en la vista de tabla mediante los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7bbd7-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="7bbd7-177">No hay ningún límite en el número de elementos [TypeName](./typename-element-for-viewselectedby-format.md) que se pueden especificar y su orden no es significativo.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="7bbd7-178">Los siguientes elementos XML se pueden utilizar para especificar los objetos que se usan en la vista de tabla:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="7bbd7-179">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="7bbd7-180">El elemento [TypeName](./typename-element-for-viewselectedby-format.md) especifica el objeto .net que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="7bbd7-181">El nombre completo del tipo .NET es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="7bbd7-182">Debe especificar al menos un tipo o conjunto de selección para la vista, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="7bbd7-183">En el ejemplo siguiente se usan los elementos [ViewSelectedBy](./viewselectedby-element-format.md) y [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7bbd7-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="7bbd7-184">Use conjuntos de selección en los que tenga un conjunto relacionado de objetos que se muestran mediante varias vistas, como cuando se define una vista de lista y una vista de tabla para los mismos objetos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="7bbd7-185">Para obtener más información sobre cómo crear un conjunto de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="7bbd7-186">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="7bbd7-187">El elemento [ViewSelectedBy](./viewselectedby-element-format.md) define qué objetos se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="7bbd7-188">El elemento [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) especifica un conjunto de objetos que se pueden mostrar en la vista.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="7bbd7-189">Debe especificar al menos un conjunto o tipo de selección para la vista, pero no se puede especificar un número máximo de elementos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="7bbd7-190">En el ejemplo siguiente se muestra cómo definir los objetos mostrados por una definición específica de la vista de tabla mediante el elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7bbd7-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="7bbd7-191">Con este elemento, puede especificar el nombre de tipo .NET del objeto, un conjunto de selección de objetos o una condición de selección que especifica cuándo se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="7bbd7-192">Para obtener más información sobre cómo crear condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7bbd7-193">Al crear varias definiciones de la vista de tabla, no puede especificar encabezados de columna diferentes.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="7bbd7-194">Solo puede especificar lo que se muestra en las filas de la tabla, como los objetos que se muestran.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="7bbd7-195">Los siguientes elementos XML se pueden usar para especificar los objetos que se usan en una definición específica de la vista de lista:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="7bbd7-196">El elemento [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) define qué objetos se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="7bbd7-197">El elemento [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) especifica el objeto .net que se muestra en la definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="7bbd7-198">Al usar este elemento, se requiere el nombre completo del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="7bbd7-199">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="7bbd7-200">El elemento [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica un conjunto de objetos que se pueden mostrar en esta definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="7bbd7-201">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="7bbd7-202">El elemento [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (no se muestra) especifica una condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="7bbd7-203">Debe especificar al menos un tipo, conjunto de selección o condición de selección para la definición, pero no hay ningún número máximo de elementos que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="7bbd7-204">Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7bbd7-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="7bbd7-205">Usar cadenas de formato</span><span class="sxs-lookup"><span data-stu-id="7bbd7-205">Using Format Strings</span></span>

<span data-ttu-id="7bbd7-206">Las cadenas de formato se pueden agregar a una vista para definir mejor cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="7bbd7-207">En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="7bbd7-208">Los siguientes elementos XML se pueden usar para especificar un modelo de formato:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="7bbd7-209">El elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="7bbd7-210">Se requiere un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="7bbd7-211">La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="7bbd7-212">El elemento [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica la propiedad cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="7bbd7-213">Debe especificar una propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="7bbd7-214">El elemento [FormatString](./label-element-for-listitem-for-listcontrol-format.md) especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="7bbd7-215">En el ejemplo siguiente, se llama al método `ToString` para dar formato al valor del script.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="7bbd7-216">Los scripts pueden llamar a cualquier método de un objeto.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="7bbd7-217">Por consiguiente, si un objeto tiene un método, como `ToString`, que tiene parámetros de formato, el script puede llamar a ese método para dar formato al valor de salida del script.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="7bbd7-218">El siguiente elemento XML se puede usar para llamar al método `ToString`:</span><span class="sxs-lookup"><span data-stu-id="7bbd7-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="7bbd7-219">El elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="7bbd7-220">Se requiere un elemento [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="7bbd7-221">La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="7bbd7-222">El elemento [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) especifica el script cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="7bbd7-223">Debe especificar un script o una propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7bbd7-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bbd7-224">Véase también</span><span class="sxs-lookup"><span data-stu-id="7bbd7-224">See Also</span></span>

[<span data-ttu-id="7bbd7-225">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7bbd7-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
