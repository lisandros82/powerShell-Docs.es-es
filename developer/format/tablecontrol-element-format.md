---
title: Elemento TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054584"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="36b86-102">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-102">TableControl Element (Format)</span></span>

<span data-ttu-id="36b86-103">Define un formato de tabla para obtener una vista.</span><span class="sxs-lookup"><span data-stu-id="36b86-103">Defines a table format for a view.</span></span>

<span data-ttu-id="36b86-104">Elemento ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36b86-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="36b86-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="36b86-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="36b86-106">Attributes and Elements</span></span>

<span data-ttu-id="36b86-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="36b86-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="36b86-108">Debe especificar las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="36b86-108">You must specify the rows of the table.</span></span> <span data-ttu-id="36b86-109">Todos los demás elementos secundarios son opcionales.</span><span class="sxs-lookup"><span data-stu-id="36b86-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="36b86-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="36b86-110">Attributes</span></span>

<span data-ttu-id="36b86-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="36b86-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36b86-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="36b86-112">Child Elements</span></span>

|<span data-ttu-id="36b86-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="36b86-113">Element</span></span>|<span data-ttu-id="36b86-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="36b86-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36b86-115">Elemento AutoSize para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="36b86-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="36b86-116">Optional element.</span></span><br /><br /> <span data-ttu-id="36b86-117">Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="36b86-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="36b86-118">Elemento HideTableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="36b86-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="36b86-119">Optional element.</span></span><br /><br /> <span data-ttu-id="36b86-120">Indica si el encabezado de la tabla no se muestra.</span><span class="sxs-lookup"><span data-stu-id="36b86-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="36b86-121">Elemento TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="36b86-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="36b86-122">Required element.</span></span><br /><br /> <span data-ttu-id="36b86-123">Define las etiquetas, el ancho y la alineación de los datos para las columnas de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="36b86-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="36b86-124">Elemento TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="36b86-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="36b86-125">Optional element.</span></span><br /><br /> <span data-ttu-id="36b86-126">Proporciona las definiciones de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="36b86-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36b86-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="36b86-127">Parent Elements</span></span>

|<span data-ttu-id="36b86-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="36b86-128">Element</span></span>|<span data-ttu-id="36b86-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="36b86-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36b86-130">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="36b86-131">Define una vista que se usa para mostrar a los miembros de uno o varios objetos.</span><span class="sxs-lookup"><span data-stu-id="36b86-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="36b86-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="36b86-132">Remarks</span></span>

<span data-ttu-id="36b86-133">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="36b86-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="36b86-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="36b86-134">Example</span></span>

<span data-ttu-id="36b86-135">Este ejemplo se muestra un `TableControl` elemento que se utiliza para mostrar las propiedades de la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="36b86-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="36b86-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="36b86-136">See Also</span></span>

[<span data-ttu-id="36b86-137">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="36b86-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="36b86-138">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="36b86-139">Elemento AutoSize para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="36b86-140">Elemento HideTableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="36b86-141">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="36b86-142">Elemento TableRowEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="36b86-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="36b86-143">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="36b86-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
