---
title: Elemento Label para TableColumnHeader para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365174"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="e2567-102">Elemento Label para TableColumnHeader for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e2567-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="e2567-103">Define la etiqueta que se muestra en la parte superior de una columna.</span><span class="sxs-lookup"><span data-stu-id="e2567-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="e2567-104">Este elemento se utiliza al definir una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="e2567-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="e2567-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format) TableColumnHeader Element for TableHeaders for Tablecontrol ((Format) Label Element for TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="e2567-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2567-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e2567-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2567-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e2567-107">Attributes and Elements</span></span>

<span data-ttu-id="e2567-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Label`.</span><span class="sxs-lookup"><span data-stu-id="e2567-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="e2567-109">Solo se permite una etiqueta para cada columna.</span><span class="sxs-lookup"><span data-stu-id="e2567-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2567-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e2567-110">Attributes</span></span>

<span data-ttu-id="e2567-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e2567-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2567-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e2567-112">Child Elements</span></span>

<span data-ttu-id="e2567-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e2567-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2567-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e2567-114">Parent Elements</span></span>

|<span data-ttu-id="e2567-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e2567-115">Element</span></span>|<span data-ttu-id="e2567-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="e2567-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2567-117">Elemento TableColumnHeader para TableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="e2567-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="e2567-118">Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="e2567-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2567-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e2567-119">Text Value</span></span>

<span data-ttu-id="e2567-120">Especifique el texto que se muestra en la parte superior de la columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="e2567-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="e2567-121">No hay caracteres restringidos para la etiqueta de columna.</span><span class="sxs-lookup"><span data-stu-id="e2567-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2567-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e2567-122">Remarks</span></span>

<span data-ttu-id="e2567-123">Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.</span><span class="sxs-lookup"><span data-stu-id="e2567-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="e2567-124">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2567-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e2567-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e2567-125">Example</span></span>

<span data-ttu-id="e2567-126">En este ejemplo se muestra un elemento `TableColumnHeader` cuya etiqueta es "Column 1".</span><span class="sxs-lookup"><span data-stu-id="e2567-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="e2567-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="e2567-127">See Also</span></span>

[<span data-ttu-id="e2567-128">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="e2567-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e2567-129">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="e2567-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="e2567-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2567-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
