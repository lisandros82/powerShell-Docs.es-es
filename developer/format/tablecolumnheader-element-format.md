---
title: Elemento TableColumnHeader (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858601"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="71574-102">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="71574-103">Define la etiqueta, el ancho de la columna y la alineación de la etiqueta de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="71574-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="71574-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuración (elemento) TableColumnHeader TableControl (formato) para TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71574-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="71574-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71574-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="71574-106">Attributes and Elements</span></span>

<span data-ttu-id="71574-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TableColumnHeader` elemento.</span><span class="sxs-lookup"><span data-stu-id="71574-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71574-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="71574-108">Attributes</span></span>

<span data-ttu-id="71574-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="71574-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71574-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="71574-110">Child Elements</span></span>

|<span data-ttu-id="71574-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="71574-111">Element</span></span>|<span data-ttu-id="71574-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="71574-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71574-113">Elemento de etiqueta para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="71574-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="71574-114">Optional element.</span></span><br /><br /> <span data-ttu-id="71574-115">Define la etiqueta que se muestra en la parte superior de la columna.</span><span class="sxs-lookup"><span data-stu-id="71574-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="71574-116">Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.</span><span class="sxs-lookup"><span data-stu-id="71574-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="71574-117">Elemento de ancho para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="71574-118">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="71574-118">Required element.</span></span><br /><br /> <span data-ttu-id="71574-119">Especifica el ancho (en caracteres) de la columna.</span><span class="sxs-lookup"><span data-stu-id="71574-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="71574-120">Elemento Alignment para TableColumbnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="71574-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="71574-121">Optional element.</span></span><br /><br /> <span data-ttu-id="71574-122">Especifica cómo se muestra la etiqueta de la columna.</span><span class="sxs-lookup"><span data-stu-id="71574-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="71574-123">Si no se especifica ninguna alineación, la etiqueta se alinea a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="71574-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="71574-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="71574-124">Parent Elements</span></span>

|<span data-ttu-id="71574-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="71574-125">Element</span></span>|<span data-ttu-id="71574-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="71574-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71574-127">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="71574-128">Define las columnas de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="71574-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="71574-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="71574-129">Remarks</span></span>

<span data-ttu-id="71574-130">Especificar un encabezado para cada columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="71574-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="71574-131">Las columnas se muestran en el orden en que el `TableColumnHeader` se definen los elementos.</span><span class="sxs-lookup"><span data-stu-id="71574-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="71574-132">Una tabla debe tener el mismo número de `TableColumnHeader` elementos como `TableRowEntry` elementos.</span><span class="sxs-lookup"><span data-stu-id="71574-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="71574-133">El encabezado de columna define cómo se muestra el texto en la parte superior de la tabla.</span><span class="sxs-lookup"><span data-stu-id="71574-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="71574-134">Las entradas de fila definen qué datos se muestran en las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="71574-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="71574-135">Para obtener más información acerca de los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="71574-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="71574-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="71574-136">Example</span></span>

<span data-ttu-id="71574-137">El ejemplo siguiente muestra dos `TableColumnHeader` elementos.</span><span class="sxs-lookup"><span data-stu-id="71574-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="71574-138">El primer elemento define una columna cuya etiqueta es "Columna 1", tiene un ancho de 16 caracteres, y cuya etiqueta se alinea a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="71574-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="71574-139">El segundo elemento define una columna cuya etiqueta es "Columna 2", tiene un ancho de 10 caracteres, y cuya etiqueta se centra en la columna.</span><span class="sxs-lookup"><span data-stu-id="71574-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="71574-140">Véase también</span><span class="sxs-lookup"><span data-stu-id="71574-140">See Also</span></span>

[<span data-ttu-id="71574-141">Elemento Alignment para TableColumnHeader para TableContrl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="71574-142">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="71574-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="71574-143">Elemento de etiqueta para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="71574-144">Elemento TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="71574-145">Ancho del TableColumnHeader elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71574-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="71574-146">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="71574-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
