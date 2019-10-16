---
title: Elemento TableHeaders (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361824"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="8eca0-102">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="8eca0-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="8eca0-103">Define los encabezados de las columnas de una tabla.</span><span class="sxs-lookup"><span data-stu-id="8eca0-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="8eca0-104">Elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="8eca0-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8eca0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8eca0-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8eca0-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8eca0-106">Attributes and Elements</span></span>

<span data-ttu-id="8eca0-107">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `TableHeaders`.</span><span class="sxs-lookup"><span data-stu-id="8eca0-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="8eca0-108">Debe haber un elemento secundario para cada propiedad del objeto que se va a mostrar.</span><span class="sxs-lookup"><span data-stu-id="8eca0-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="8eca0-109">La información del encabezado de columna se muestra en el orden en que se especifican los elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="8eca0-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="8eca0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8eca0-110">Attributes</span></span>

<span data-ttu-id="8eca0-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8eca0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8eca0-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8eca0-112">Child Elements</span></span>

|<span data-ttu-id="8eca0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8eca0-113">Element</span></span>|<span data-ttu-id="8eca0-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="8eca0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eca0-115">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="8eca0-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="8eca0-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8eca0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8eca0-117">Define la etiqueta, el ancho y la alineación de los datos de una columna de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="8eca0-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8eca0-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8eca0-118">Parent Elements</span></span>

|<span data-ttu-id="8eca0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8eca0-119">Element</span></span>|<span data-ttu-id="8eca0-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="8eca0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eca0-121">Elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="8eca0-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="8eca0-122">Define un formato de tabla para una vista.</span><span class="sxs-lookup"><span data-stu-id="8eca0-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8eca0-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8eca0-123">Remarks</span></span>

<span data-ttu-id="8eca0-124">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8eca0-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8eca0-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8eca0-125">Example</span></span>

<span data-ttu-id="8eca0-126">En este ejemplo se muestra un elemento `TableHeaders` que define dos encabezados de columna.</span><span class="sxs-lookup"><span data-stu-id="8eca0-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="8eca0-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="8eca0-127">See Also</span></span>

[<span data-ttu-id="8eca0-128">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="8eca0-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8eca0-129">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="8eca0-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="8eca0-130">Elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="8eca0-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="8eca0-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8eca0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
