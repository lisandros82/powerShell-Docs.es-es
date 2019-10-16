---
title: Información general sobre el formato de archivo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363694"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="54dee-102">Información general del archivo de formato</span><span class="sxs-lookup"><span data-stu-id="54dee-102">Formatting File Overview</span></span>

<span data-ttu-id="54dee-103">El formato de presentación de los objetos devueltos por los comandos (cmdlets, funciones y scripts) se define mediante el uso de archivos de formato (archivos Format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="54dee-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="54dee-104">PowerShell proporciona algunos de estos archivos para definir el formato de presentación de los objetos devueltos por los comandos proporcionados por PowerShell, como el objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) devuelto por el cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="54dee-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="54dee-105">Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminados o puede escribir un archivo de formato personalizado para definir la presentación de los objetos devueltos por sus propios comandos.</span><span class="sxs-lookup"><span data-stu-id="54dee-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54dee-106">Los archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización.</span><span class="sxs-lookup"><span data-stu-id="54dee-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="54dee-107">Cuando se devuelve un objeto a la canalización, todos los miembros de ese objeto están disponibles aunque no se muestren algunos.</span><span class="sxs-lookup"><span data-stu-id="54dee-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="54dee-108">PowerShell usa los datos de estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos mostrados.</span><span class="sxs-lookup"><span data-stu-id="54dee-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="54dee-109">Los datos mostrados pueden incluir las propiedades de un objeto o el valor de un script.</span><span class="sxs-lookup"><span data-stu-id="54dee-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="54dee-110">Los scripts se usan si desea mostrar algún valor que no está disponible directamente desde las propiedades de un objeto, como agregar el valor de dos propiedades de un objeto y, a continuación, Mostrar la suma como una parte de los datos.</span><span class="sxs-lookup"><span data-stu-id="54dee-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="54dee-111">El formato de los datos mostrados se realiza definiendo vistas para los objetos que desea mostrar.</span><span class="sxs-lookup"><span data-stu-id="54dee-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="54dee-112">Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="54dee-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="54dee-113">No hay ningún límite en el número de vistas que puede definir.</span><span class="sxs-lookup"><span data-stu-id="54dee-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="54dee-114">Características comunes de los archivos de formato</span><span class="sxs-lookup"><span data-stu-id="54dee-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="54dee-115">Cada archivo de formato puede definir los siguientes componentes que se pueden compartir entre todas las vistas definidas por el archivo:</span><span class="sxs-lookup"><span data-stu-id="54dee-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="54dee-116">Valor de configuración predeterminado, como si los datos mostrados en las filas de las tablas se van a mostrar en la línea siguiente si los datos son más largos que el ancho de la columna.</span><span class="sxs-lookup"><span data-stu-id="54dee-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="54dee-117">Para obtener más información acerca de esta configuración, consulte [definir opciones de configuración comunes](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="54dee-118">Conjuntos de objetos que se pueden mostrar en cualquiera de las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="54dee-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="54dee-119">Para obtener más información acerca de estos conjuntos (denominados *conjuntos de selección*), consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="54dee-120">Controles comunes que se pueden usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="54dee-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="54dee-121">Los controles proporcionan un control más preciso sobre cómo se muestran los datos.</span><span class="sxs-lookup"><span data-stu-id="54dee-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="54dee-122">Para obtener más información sobre los controles, vea [definir controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="54dee-123">Dar formato a vistas</span><span class="sxs-lookup"><span data-stu-id="54dee-123">Formatting Views</span></span>

<span data-ttu-id="54dee-124">Las vistas de formato pueden mostrar objetos en formato de tabla, formato de lista, formato ancho y formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="54dee-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="54dee-125">En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen la vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="54dee-126">Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y de fila de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="54dee-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="54dee-127">Vista de tabla enumera las propiedades de un objeto o un valor de bloque de script en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="54dee-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="54dee-128">Cada columna representa una única propiedad del objeto o un valor de script.</span><span class="sxs-lookup"><span data-stu-id="54dee-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="54dee-129">Puede definir una vista de tabla que muestre todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores de script.</span><span class="sxs-lookup"><span data-stu-id="54dee-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="54dee-130">Cada fila de la tabla representa un objeto devuelto.</span><span class="sxs-lookup"><span data-stu-id="54dee-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="54dee-131">Crear una vista de tabla es muy similar a cuando se canaliza un objeto al cmdlet `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="54dee-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="54dee-132">Para obtener más información sobre esta vista, vea [vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="54dee-133">Vista de lista muestra las propiedades de un objeto o un valor de script en una sola columna.</span><span class="sxs-lookup"><span data-stu-id="54dee-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="54dee-134">Cada fila de la lista muestra una etiqueta opcional o el nombre de la propiedad seguido del valor de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="54dee-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="54dee-135">Crear una vista de lista es muy similar a canalizar un objeto al cmdlet `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="54dee-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="54dee-136">Para obtener más información sobre esta vista, vea [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="54dee-137">Vista ancha muestra una única propiedad de un objeto o un valor de script en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="54dee-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="54dee-138">No hay etiqueta o encabezado para esta vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-138">There is no label or header for this view.</span></span> <span data-ttu-id="54dee-139">La creación de una vista amplia es muy similar a la canalización de un objeto al cmdlet `Format-Wide`.</span><span class="sxs-lookup"><span data-stu-id="54dee-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="54dee-140">Para obtener más información sobre esta vista, vea [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="54dee-141">Vista personalizada muestra una vista personalizable de las propiedades de objeto o de los valores de script que no se adhiere a la estructura rígida de las vistas de tabla, las vistas de lista o las vistas anchas.</span><span class="sxs-lookup"><span data-stu-id="54dee-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="54dee-142">Puede definir una vista personalizada independiente o puede definir una vista personalizada que se use en otra vista, como una vista de tabla o una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="54dee-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="54dee-143">La creación de una vista personalizada es muy similar a la canalización de un objeto al cmdlet `Format-Custom`.</span><span class="sxs-lookup"><span data-stu-id="54dee-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="54dee-144">Para obtener más información acerca de esta vista, vea [vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="54dee-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="54dee-145">Componentes de una vista</span><span class="sxs-lookup"><span data-stu-id="54dee-145">Components of a View</span></span>

<span data-ttu-id="54dee-146">En los siguientes ejemplos XML se muestran los componentes XML básicos de una vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="54dee-147">Los elementos XML individuales varían en función de la vista que desea crear, pero los componentes básicos de las vistas son los mismos.</span><span class="sxs-lookup"><span data-stu-id="54dee-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="54dee-148">Para empezar, cada vista tiene un elemento `Name` que especifica un nombre descriptivo que se usa para hacer referencia a la vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="54dee-149">un elemento `ViewSelectedBy` que define qué objetos .NET se muestran en la vista, y un elemento de *control* que define la vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="54dee-150">Dentro del elemento de control, puede definir uno o varios elementos de *entrada* .</span><span class="sxs-lookup"><span data-stu-id="54dee-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="54dee-151">Si usa varias definiciones, debe especificar qué objetos .NET usan cada definición.</span><span class="sxs-lookup"><span data-stu-id="54dee-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="54dee-152">Normalmente, solo se necesita una entrada, con una sola definición, para cada control.</span><span class="sxs-lookup"><span data-stu-id="54dee-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="54dee-153">Dentro de cada elemento de entrada de una vista, se especifican *los elementos que* definen las propiedades o los scripts .net que se muestran en esa vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="54dee-154">Como se muestra en los ejemplos anteriores, el archivo de formato puede contener varias vistas, una vista puede contener varias definiciones y cada definición puede contener varios elementos.</span><span class="sxs-lookup"><span data-stu-id="54dee-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="54dee-155">Ejemplo de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="54dee-155">Example of a Table View</span></span>

<span data-ttu-id="54dee-156">En el ejemplo siguiente se muestran las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas.</span><span class="sxs-lookup"><span data-stu-id="54dee-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="54dee-157">El elemento [ViewDefinitions](./viewdefinitions-element-format.md) es el elemento contenedor de todas las vistas definidas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="54dee-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="54dee-158">El elemento de [vista](./view-element-format.md) define la vista de tabla, lista, ancho o personalizada específica.</span><span class="sxs-lookup"><span data-stu-id="54dee-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="54dee-159">Dentro de cada elemento de [vista](./view-element-format.md) , el elemento [Name](./name-element-for-view-format.md) especifica el nombre de la vista, el elemento [ViewSelectedBy](./viewselectedby-element-format.md) define los objetos que utilizan la vista y los distintos elementos de control (como el elemento `TableControl` que se muestra en la siguiente ejemplo) defina el tipo de la vista.</span><span class="sxs-lookup"><span data-stu-id="54dee-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="54dee-160">Véase también</span><span class="sxs-lookup"><span data-stu-id="54dee-160">See Also</span></span>

[<span data-ttu-id="54dee-161">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="54dee-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="54dee-162">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="54dee-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="54dee-163">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="54dee-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="54dee-164">Crear controles personalizados</span><span class="sxs-lookup"><span data-stu-id="54dee-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="54dee-165">Escribir un archivo de formato y tipos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="54dee-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
