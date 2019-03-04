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
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858921"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="1479d-102">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-102">TableControl Element (Format)</span></span>

<span data-ttu-id="1479d-103">Define un formato de tabla para obtener una vista.</span><span class="sxs-lookup"><span data-stu-id="1479d-103">Defines a table format for a view.</span></span>

<span data-ttu-id="1479d-104">Elemento ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1479d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1479d-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1479d-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1479d-106">Attributes and Elements</span></span>

<span data-ttu-id="1479d-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="1479d-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="1479d-108">Debe especificar las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="1479d-108">You must specify the rows of the table.</span></span> <span data-ttu-id="1479d-109">Todos los demás elementos secundarios son opcionales.</span><span class="sxs-lookup"><span data-stu-id="1479d-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="1479d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1479d-110">Attributes</span></span>

<span data-ttu-id="1479d-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1479d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1479d-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1479d-112">Child Elements</span></span>

|<span data-ttu-id="1479d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1479d-113">Element</span></span>|<span data-ttu-id="1479d-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="1479d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1479d-115">Elemento AutoSize para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="1479d-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1479d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1479d-117">Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="1479d-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="1479d-118">Elemento HideTableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="1479d-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1479d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1479d-120">Indica si el encabezado de la tabla no se muestra.</span><span class="sxs-lookup"><span data-stu-id="1479d-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="1479d-121">Elemento TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="1479d-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="1479d-122">Required element.</span></span><br /><br /> <span data-ttu-id="1479d-123">Define las etiquetas, el ancho y la alineación de los datos para las columnas de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="1479d-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="1479d-124">Elemento TableRowEntries para TableCotrol (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-124">TableRowEntries Element for TableCotrol (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="1479d-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1479d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1479d-126">Proporciona las definiciones de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="1479d-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1479d-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1479d-127">Parent Elements</span></span>

|<span data-ttu-id="1479d-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1479d-128">Element</span></span>|<span data-ttu-id="1479d-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="1479d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1479d-130">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1479d-131">Define una vista que se usa para mostrar a los miembros de uno o varios objetos.</span><span class="sxs-lookup"><span data-stu-id="1479d-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1479d-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1479d-132">Remarks</span></span>

<span data-ttu-id="1479d-133">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1479d-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1479d-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1479d-134">Example</span></span>

<span data-ttu-id="1479d-135">Este ejemplo se muestra un `TableControl` elemento que se utiliza para mostrar las propiedades de la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="1479d-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1479d-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="1479d-136">See Also</span></span>

[<span data-ttu-id="1479d-137">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="1479d-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1479d-138">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="1479d-139">Elemento AutoSize para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="1479d-140">Elemento HideTableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="1479d-141">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="1479d-142">Elemento TableRowEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="1479d-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="1479d-143">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1479d-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
