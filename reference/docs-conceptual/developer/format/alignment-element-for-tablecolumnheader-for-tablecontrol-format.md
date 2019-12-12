---
title: Elemento Alignment para TableColumnHeader para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364384"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="59853-102">Elemento Alignment para TableColumnHeader for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="59853-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="59853-103">Define cómo se muestran los datos en un encabezado de columna.</span><span class="sxs-lookup"><span data-stu-id="59853-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="59853-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders (Format) elemento TableColumnHeader (Format) Alignment for TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="59853-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59853-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="59853-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59853-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="59853-106">Attributes and Elements</span></span>

<span data-ttu-id="59853-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Alignment`.</span><span class="sxs-lookup"><span data-stu-id="59853-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="59853-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="59853-108">Attributes</span></span>

<span data-ttu-id="59853-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="59853-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59853-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="59853-110">Child Elements</span></span>

<span data-ttu-id="59853-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="59853-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59853-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="59853-112">Parent Elements</span></span>

|<span data-ttu-id="59853-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="59853-113">Element</span></span>|<span data-ttu-id="59853-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="59853-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59853-115">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="59853-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="59853-116">Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="59853-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="59853-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="59853-117">Text Value</span></span>

<span data-ttu-id="59853-118">Especifique uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="59853-118">Specify one of the following values.</span></span> <span data-ttu-id="59853-119">Estos valores no distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="59853-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="59853-120">Left alinea los datos mostrados en la columna de la izquierda este es el valor predeterminado si no se especifica este elemento.</span><span class="sxs-lookup"><span data-stu-id="59853-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="59853-121">Alinea a la derecha los datos mostrados en la columna de la derecha.</span><span class="sxs-lookup"><span data-stu-id="59853-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="59853-122">Center centra los datos mostrados en la columna.</span><span class="sxs-lookup"><span data-stu-id="59853-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="59853-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="59853-123">Remarks</span></span>

<span data-ttu-id="59853-124">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="59853-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="59853-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="59853-125">Example</span></span>

<span data-ttu-id="59853-126">En este ejemplo se muestra un elemento `TableColumnHeader` cuyos datos se alinean a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="59853-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="59853-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="59853-127">See Also</span></span>

[<span data-ttu-id="59853-128">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="59853-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="59853-129">Elemento TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="59853-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="59853-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="59853-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
