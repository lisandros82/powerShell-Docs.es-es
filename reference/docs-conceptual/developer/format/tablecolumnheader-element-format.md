---
title: Elemento TableColumnHeader (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361854"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="fb5ea-102">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="fb5ea-103">Define la etiqueta, el ancho de la columna y la alineación de la etiqueta para una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="fb5ea-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format) elemento TableColumnHeader para TableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb5ea-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fb5ea-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb5ea-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fb5ea-106">Attributes and Elements</span></span>

<span data-ttu-id="fb5ea-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb5ea-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb5ea-108">Attributes</span></span>

<span data-ttu-id="fb5ea-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb5ea-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fb5ea-110">Child Elements</span></span>

|<span data-ttu-id="fb5ea-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb5ea-111">Element</span></span>|<span data-ttu-id="fb5ea-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb5ea-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb5ea-113">Elemento Label para TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="fb5ea-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-114">Optional element.</span></span><br /><br /> <span data-ttu-id="fb5ea-115">Define la etiqueta que se muestra en la parte superior de la columna.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="fb5ea-116">Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="fb5ea-117">Elemento width para TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="fb5ea-118">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-118">Required element.</span></span><br /><br /> <span data-ttu-id="fb5ea-119">Especifica el ancho (en caracteres) de la columna.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="fb5ea-120">Elemento Alignment para TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="fb5ea-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-121">Optional element.</span></span><br /><br /> <span data-ttu-id="fb5ea-122">Especifica cómo se muestra la etiqueta de la columna.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="fb5ea-123">Si no se especifica ninguna alineación, la etiqueta se alinea a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fb5ea-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fb5ea-124">Parent Elements</span></span>

|<span data-ttu-id="fb5ea-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb5ea-125">Element</span></span>|<span data-ttu-id="fb5ea-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb5ea-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb5ea-127">Elemento TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="fb5ea-128">Define las columnas de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb5ea-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fb5ea-129">Remarks</span></span>

<span data-ttu-id="fb5ea-130">Especifique un encabezado para cada columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="fb5ea-131">Las columnas se muestran en el orden en el que se definen los elementos `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="fb5ea-132">Una tabla debe tener el mismo número de elementos `TableColumnHeader` que `TableRowEntry`.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="fb5ea-133">El encabezado de columna define cómo se muestra el texto en la parte superior de la tabla.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="fb5ea-134">Las entradas de fila definen qué datos se muestran en las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="fb5ea-135">Para obtener más información sobre los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fb5ea-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fb5ea-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fb5ea-136">Example</span></span>

<span data-ttu-id="fb5ea-137">En el ejemplo siguiente se muestran dos elementos `TableColumnHeader`.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="fb5ea-138">El primer elemento define una columna cuya etiqueta es "columna 1", tiene un ancho de 16 caracteres y cuya etiqueta está alineada a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="fb5ea-139">El segundo elemento define una columna cuya etiqueta es "columna 2", tiene un ancho de 10 caracteres y cuya etiqueta está centrada en la columna.</span><span class="sxs-lookup"><span data-stu-id="fb5ea-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fb5ea-140">Véase también</span><span class="sxs-lookup"><span data-stu-id="fb5ea-140">See Also</span></span>

[<span data-ttu-id="fb5ea-141">Elemento Alignment para TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="fb5ea-142">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="fb5ea-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fb5ea-143">Elemento Label para TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="fb5ea-144">Elemento TableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="fb5ea-145">Width para TableColumnHeader para el elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fb5ea-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="fb5ea-146">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb5ea-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
