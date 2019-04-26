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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068307"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="d96b3-102">Archivos de formato personalizado</span><span class="sxs-lookup"><span data-stu-id="d96b3-102">Custom Formatting Files</span></span>

<span data-ttu-id="d96b3-103">El formato de presentación de los objetos devueltos por los cmdlets, funciones y scripts se definen mediante archivos de formato (archivos format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="d96b3-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="d96b3-104">Algunos de estos archivos se proporcionan con Windows PowerShell para definir el formato de presentación predeterminado para los objetos devueltos por los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d96b3-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="d96b3-105">Sin embargo, también puede crear sus propios archivos de formato personalizados para sobrescribir los formatos de presentación predeterminado o para definir la presentación de los objetos devueltos por sus propios comandos.</span><span class="sxs-lookup"><span data-stu-id="d96b3-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="d96b3-106">Windows PowerShell usa los datos en estos archivos de formato para determinar lo que se muestra y cómo se da formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="d96b3-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="d96b3-107">Pueden incluir los datos que se muestran las propiedades de un objeto o el valor de un bloque de script.</span><span class="sxs-lookup"><span data-stu-id="d96b3-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="d96b3-108">Si desea mostrar un valor que no está disponible directamente desde las propiedades de un objeto, se utilizan bloques de script.</span><span class="sxs-lookup"><span data-stu-id="d96b3-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="d96b3-109">Por ejemplo, es posible que desee agregar el valor de dos propiedades de un objeto y mostrar la suma como una hoja de datos independiente.</span><span class="sxs-lookup"><span data-stu-id="d96b3-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="d96b3-110">Al escribir su propio formato de archivo, deberá definir *vistas* para los objetos que desea mostrar.</span><span class="sxs-lookup"><span data-stu-id="d96b3-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="d96b3-111">Puede definir una vista única para cada objeto, puede definir una vista única para varios objetos o puede definir varias vistas para el mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="d96b3-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="d96b3-112">No hay ningún límite al número de vistas que se pueden definir.</span><span class="sxs-lookup"><span data-stu-id="d96b3-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d96b3-113">Archivos de formato no determinan los elementos de un objeto que se devuelven a la canalización.</span><span class="sxs-lookup"><span data-stu-id="d96b3-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="d96b3-114">Cuando se devuelve un objeto a la canalización, están disponibles todos los miembros de ese objeto.</span><span class="sxs-lookup"><span data-stu-id="d96b3-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="d96b3-115">Vistas de formato</span><span class="sxs-lookup"><span data-stu-id="d96b3-115">Format Views</span></span>

<span data-ttu-id="d96b3-116">Formato de las vistas pueden mostrar los objetos en un formato de tabla, un formato de lista, un formato ancho y un formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="d96b3-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="d96b3-117">En su mayor parte, cada definición de formato se describe mediante un conjunto de etiquetas XML que describen una vista.</span><span class="sxs-lookup"><span data-stu-id="d96b3-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="d96b3-118">Cada vista contiene el nombre de la vista, los objetos que utilizan la vista y los elementos de la vista, como la información de columna y fila de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="d96b3-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="d96b3-119">Las vistas siguientes están disponibles.</span><span class="sxs-lookup"><span data-stu-id="d96b3-119">The following views are available.</span></span>

<span data-ttu-id="d96b3-120">Vista de tabla enumera las propiedades de un objeto o un valor de bloque de script en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="d96b3-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d96b3-121">Cada columna representa una propiedad del objeto o un valor de bloque de script.</span><span class="sxs-lookup"><span data-stu-id="d96b3-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="d96b3-122">Puede definir una vista de tabla que muestra todas las propiedades de un objeto, un subconjunto de las propiedades de un objeto o una combinación de propiedades y valores del bloque de script.</span><span class="sxs-lookup"><span data-stu-id="d96b3-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="d96b3-123">Cada fila de la tabla representa un objeto devuelto.</span><span class="sxs-lookup"><span data-stu-id="d96b3-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="d96b3-124">Para obtener más información sobre esta vista, consulte [vista de tabla](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d96b3-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="d96b3-125">Vista de lista enumera las propiedades de un objeto o un valor de bloque de script en una sola columna.</span><span class="sxs-lookup"><span data-stu-id="d96b3-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="d96b3-126">Cada fila de la lista muestra una etiqueta opcional o el nombre de propiedad seguido por el valor de la propiedad o bloque de script.</span><span class="sxs-lookup"><span data-stu-id="d96b3-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="d96b3-127">Para obtener más información sobre esta vista, consulte [vista de lista](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d96b3-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="d96b3-128">Vista ampliada muestra una propiedad única de un objeto o un valor de bloque de script en una o varias columnas.</span><span class="sxs-lookup"><span data-stu-id="d96b3-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d96b3-129">No hay ninguna etiqueta ni el encabezado para esta vista.</span><span class="sxs-lookup"><span data-stu-id="d96b3-129">There is no label or header for this view.</span></span> <span data-ttu-id="d96b3-130">Para obtener más información sobre esta vista, consulte [vista amplia](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d96b3-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="d96b3-131">Vista personalizada muestra una vista personalizable de las propiedades del objeto o los valores del bloque de script que no se adhiere a la estructura rígida de las vistas de tablas, vistas de lista o vista amplia.</span><span class="sxs-lookup"><span data-stu-id="d96b3-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="d96b3-132">Puede definir una vista personalizada independiente, o puede definir una vista personalizada que está usando otra vista, como una vista de tabla o vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d96b3-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="d96b3-133">Para obtener más información sobre esta vista, consulte [vista personalizada](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d96b3-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="d96b3-134">Elementos de la vista XML</span><span class="sxs-lookup"><span data-stu-id="d96b3-134">View XML Elements</span></span>

<span data-ttu-id="d96b3-135">El ejemplo siguiente muestra las etiquetas XML utilizadas para definir una vista de tabla que contiene dos columnas.</span><span class="sxs-lookup"><span data-stu-id="d96b3-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="d96b3-136">El [ViewDefinitions](../format/viewdefinitions-element-format.md) es el elemento contenedor para todas las vistas definidas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="d96b3-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="d96b3-137">El [vista](../format/view-element-format.md) elemento define la tabla específica, lista, vista amplia o personalizada.</span><span class="sxs-lookup"><span data-stu-id="d96b3-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="d96b3-138">Dentro de cada vista, el [nombre](../format/name-element-for-view-format.md) elemento especifica el nombre de la vista, el [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento define los objetos que utilizan la vista y los elementos de control diferente (como el `TableControl` elemento) define el formato de la vista.</span><span class="sxs-lookup"><span data-stu-id="d96b3-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d96b3-139">Véase también</span><span class="sxs-lookup"><span data-stu-id="d96b3-139">See Also</span></span>

[<span data-ttu-id="d96b3-140">Vista de tabla</span><span class="sxs-lookup"><span data-stu-id="d96b3-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="d96b3-141">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="d96b3-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="d96b3-142">Vista ampliada</span><span class="sxs-lookup"><span data-stu-id="d96b3-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="d96b3-143">Vista personalizada</span><span class="sxs-lookup"><span data-stu-id="d96b3-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="d96b3-144">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d96b3-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
