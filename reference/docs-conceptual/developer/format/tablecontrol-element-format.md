---
title: Elemento Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368204"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="0ab77-102">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0ab77-102">TableControl Element (Format)</span></span>

<span data-ttu-id="0ab77-103">Define un formato de tabla para una vista.</span><span class="sxs-lookup"><span data-stu-id="0ab77-103">Defines a table format for a view.</span></span>

<span data-ttu-id="0ab77-104">Elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ab77-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0ab77-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ab77-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0ab77-106">Attributes and Elements</span></span>

<span data-ttu-id="0ab77-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableControl`.</span><span class="sxs-lookup"><span data-stu-id="0ab77-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="0ab77-108">Debe especificar las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="0ab77-108">You must specify the rows of the table.</span></span> <span data-ttu-id="0ab77-109">Todos los demás elementos secundarios son opcionales.</span><span class="sxs-lookup"><span data-stu-id="0ab77-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ab77-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ab77-110">Attributes</span></span>

<span data-ttu-id="0ab77-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0ab77-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ab77-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0ab77-112">Child Elements</span></span>

|<span data-ttu-id="0ab77-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ab77-113">Element</span></span>|<span data-ttu-id="0ab77-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="0ab77-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ab77-115">AutoSize (elemento) para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="0ab77-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0ab77-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0ab77-117">Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="0ab77-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="0ab77-118">Elemento HideTableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="0ab77-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0ab77-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0ab77-120">Indica si no se muestra el encabezado de la tabla.</span><span class="sxs-lookup"><span data-stu-id="0ab77-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="0ab77-121">Elemento TableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="0ab77-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="0ab77-122">Required element.</span></span><br /><br /> <span data-ttu-id="0ab77-123">Define las etiquetas, el ancho y la alineación de los datos para las columnas de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="0ab77-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="0ab77-124">Elemento TableRowEntries para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="0ab77-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0ab77-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0ab77-126">Proporciona las definiciones de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="0ab77-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ab77-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0ab77-127">Parent Elements</span></span>

|<span data-ttu-id="0ab77-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ab77-128">Element</span></span>|<span data-ttu-id="0ab77-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="0ab77-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ab77-130">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="0ab77-131">Define una vista que se utiliza para mostrar los miembros de uno o más objetos.</span><span class="sxs-lookup"><span data-stu-id="0ab77-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ab77-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0ab77-132">Remarks</span></span>

<span data-ttu-id="0ab77-133">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0ab77-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ab77-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0ab77-134">Example</span></span>

<span data-ttu-id="0ab77-135">En este ejemplo se muestra un elemento `TableControl` que se utiliza para mostrar las propiedades del objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="0ab77-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0ab77-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="0ab77-136">See Also</span></span>

[<span data-ttu-id="0ab77-137">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="0ab77-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0ab77-138">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="0ab77-139">AutoSize (elemento) para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="0ab77-140">Elemento HideTableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="0ab77-141">Elemento TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="0ab77-142">Elemento TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="0ab77-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="0ab77-143">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ab77-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
