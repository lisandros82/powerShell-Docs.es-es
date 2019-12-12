---
title: Archivos de formato personalizado | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369834"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="46b71-102">Archivos de formato personalizado</span><span class="sxs-lookup"><span data-stu-id="46b71-102">Custom Formatting Files</span></span>

<span data-ttu-id="46b71-103">El formato de presentación de los objetos devueltos por los cmdlets, las funciones y los scripts se define mediante archivos de formato (archivos Format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="46b71-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="46b71-104">Windows PowerShell proporciona algunos de estos archivos para definir el formato de presentación predeterminado para los objetos devueltos por los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46b71-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="46b71-105">Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminados o definir la presentación de los objetos devueltos por sus propios comandos.</span><span class="sxs-lookup"><span data-stu-id="46b71-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="46b71-106">Windows PowerShell usa los datos de estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="46b71-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="46b71-107">Los datos mostrados pueden incluir las propiedades de un objeto o el valor de un bloque de script.</span><span class="sxs-lookup"><span data-stu-id="46b71-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="46b71-108">Los bloques de scripts se usan si desea mostrar algún valor que no está disponible directamente desde las propiedades de un objeto.</span><span class="sxs-lookup"><span data-stu-id="46b71-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="46b71-109">Por ejemplo, puede que desee agregar el valor de dos propiedades de un objeto y mostrar la suma como una parte independiente de los datos.</span><span class="sxs-lookup"><span data-stu-id="46b71-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="46b71-110">Al escribir su propio archivo de formato, deberá definir *vistas* para los objetos que desea mostrar.</span><span class="sxs-lookup"><span data-stu-id="46b71-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="46b71-111">Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="46b71-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="46b71-112">No hay ningún límite en el número de vistas que puede definir.</span><span class="sxs-lookup"><span data-stu-id="46b71-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46b71-113">Los archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización.</span><span class="sxs-lookup"><span data-stu-id="46b71-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="46b71-114">Cuando se devuelve un objeto a la canalización, todos los miembros de ese objeto están disponibles.</span><span class="sxs-lookup"><span data-stu-id="46b71-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="46b71-115">Dar formato a vistas</span><span class="sxs-lookup"><span data-stu-id="46b71-115">Format Views</span></span>

<span data-ttu-id="46b71-116">Las vistas de formato pueden mostrar objetos en un formato de tabla, un formato de lista, un formato ancho y un formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="46b71-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="46b71-117">En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen una vista.</span><span class="sxs-lookup"><span data-stu-id="46b71-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="46b71-118">Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y de fila de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="46b71-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="46b71-119">Están disponibles las siguientes vistas.</span><span class="sxs-lookup"><span data-stu-id="46b71-119">The following views are available.</span></span>

<span data-ttu-id="46b71-120">Vista de tabla enumera las propiedades de un objeto o un valor de bloque de script en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="46b71-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="46b71-121">Cada columna representa una propiedad del objeto o un valor de bloque de script.</span><span class="sxs-lookup"><span data-stu-id="46b71-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="46b71-122">Puede definir una vista de tabla que muestre todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores de bloque de script.</span><span class="sxs-lookup"><span data-stu-id="46b71-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="46b71-123">Cada fila de la tabla representa un objeto devuelto.</span><span class="sxs-lookup"><span data-stu-id="46b71-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="46b71-124">Para obtener más información sobre esta vista, vea [vista de tabla](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="46b71-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="46b71-125">Vista de lista muestra las propiedades de un objeto o un valor de bloque de script en una sola columna.</span><span class="sxs-lookup"><span data-stu-id="46b71-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="46b71-126">Cada fila de la lista muestra una etiqueta opcional o el nombre de la propiedad seguido del valor de la propiedad o el bloque de script.</span><span class="sxs-lookup"><span data-stu-id="46b71-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="46b71-127">Para obtener más información sobre esta vista, vea [vista de lista](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="46b71-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="46b71-128">Vista ancha muestra una única propiedad de un objeto o un valor de bloque de script en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="46b71-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="46b71-129">No hay etiqueta o encabezado para esta vista.</span><span class="sxs-lookup"><span data-stu-id="46b71-129">There is no label or header for this view.</span></span> <span data-ttu-id="46b71-130">Para obtener más información sobre esta vista, vea [vista amplia](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="46b71-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="46b71-131">Vista personalizada muestra una vista personalizable de las propiedades de objeto o de los valores de bloque de script que no se adhiere a la estructura rígida de las vistas de tabla, vistas de lista o vistas anchas.</span><span class="sxs-lookup"><span data-stu-id="46b71-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="46b71-132">Puede definir una vista personalizada independiente o puede definir una vista personalizada que se use en otra vista, como una vista de tabla o una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="46b71-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="46b71-133">Para obtener más información acerca de esta vista, vea [vista personalizada](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="46b71-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="46b71-134">Ver elementos XML</span><span class="sxs-lookup"><span data-stu-id="46b71-134">View XML Elements</span></span>

<span data-ttu-id="46b71-135">En el ejemplo siguiente se muestran las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas.</span><span class="sxs-lookup"><span data-stu-id="46b71-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="46b71-136">El elemento [ViewDefinitions](../format/viewdefinitions-element-format.md) es el elemento contenedor de todas las vistas definidas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="46b71-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="46b71-137">El elemento de [vista](../format/view-element-format.md) define la vista de tabla, lista, ancho o personalizada específica.</span><span class="sxs-lookup"><span data-stu-id="46b71-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="46b71-138">Dentro de cada vista, el elemento [Name](../format/name-element-for-view-format.md) especifica el nombre de la vista, el elemento [ViewSelectedBy](../format/viewselectedby-element-format.md) define los objetos que utilizan la vista y los distintos elementos de control (como el elemento `TableControl`) definen el formato de la vista.</span><span class="sxs-lookup"><span data-stu-id="46b71-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
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

## <a name="see-also"></a><span data-ttu-id="46b71-139">Véase también</span><span class="sxs-lookup"><span data-stu-id="46b71-139">See Also</span></span>

[<span data-ttu-id="46b71-140">Vista de tabla</span><span class="sxs-lookup"><span data-stu-id="46b71-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="46b71-141">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="46b71-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="46b71-142">Vista amplia</span><span class="sxs-lookup"><span data-stu-id="46b71-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="46b71-143">Vista personalizada</span><span class="sxs-lookup"><span data-stu-id="46b71-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="46b71-144">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="46b71-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
