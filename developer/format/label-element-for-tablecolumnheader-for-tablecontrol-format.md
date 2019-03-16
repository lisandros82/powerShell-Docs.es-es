---
title: Etiqueta de elemento de TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054516"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="d9526-102">Elemento Label para TableColumnHeader for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d9526-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="d9526-103">Define la etiqueta que se muestra en la parte superior de una columna.</span><span class="sxs-lookup"><span data-stu-id="d9526-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="d9526-104">Este elemento se usa al definir una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="d9526-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="d9526-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuración (elemento) TableColumnHeader TableControl (formato) para TableHeaders para el elemento de etiqueta TableControl (formato) para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d9526-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9526-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d9526-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9526-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d9526-107">Attributes and Elements</span></span>

<span data-ttu-id="d9526-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="d9526-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="d9526-109">Se permite sólo una etiqueta para cada columna.</span><span class="sxs-lookup"><span data-stu-id="d9526-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9526-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9526-110">Attributes</span></span>

<span data-ttu-id="d9526-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d9526-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9526-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d9526-112">Child Elements</span></span>

<span data-ttu-id="d9526-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d9526-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9526-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d9526-114">Parent Elements</span></span>

|<span data-ttu-id="d9526-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9526-115">Element</span></span>|<span data-ttu-id="d9526-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="d9526-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9526-117">Elemento TableColumnHeader para TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d9526-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="d9526-118">Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="d9526-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d9526-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d9526-119">Text Value</span></span>

<span data-ttu-id="d9526-120">Especifique el texto que se muestra en la parte superior de la columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="d9526-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="d9526-121">No hay ningún carácter restringido para la etiqueta de columna.</span><span class="sxs-lookup"><span data-stu-id="d9526-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9526-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d9526-122">Remarks</span></span>

<span data-ttu-id="d9526-123">Si no se especifica ninguna etiqueta, se usa el nombre de la propiedad cuyo valor se muestra en las filas.</span><span class="sxs-lookup"><span data-stu-id="d9526-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="d9526-124">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9526-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d9526-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d9526-125">Example</span></span>

<span data-ttu-id="d9526-126">Este ejemplo se muestra un `TableColumnHeader` elemento cuya etiqueta es "Columna 1".</span><span class="sxs-lookup"><span data-stu-id="d9526-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="d9526-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="d9526-127">See Also</span></span>

[<span data-ttu-id="d9526-128">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="d9526-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d9526-129">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="d9526-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="d9526-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9526-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
