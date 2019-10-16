---
title: Elemento width para TableColumnHeader para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367874"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="fd4c8-102">Elemento Width para TableColumnHeader for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fd4c8-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="fd4c8-103">Define el ancho (en caracteres) de una columna.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="fd4c8-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableHeaders para Tablecontrol ((Format) TableColumnHeader Element TableHeaders for Tablecontrol ((Format) width (elemento) para TableColumnHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fd4c8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd4c8-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fd4c8-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd4c8-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fd4c8-106">Attributes and Elements</span></span>

<span data-ttu-id="fd4c8-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Width` que se usa al definir los encabezados de columna.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd4c8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fd4c8-108">Attributes</span></span>

<span data-ttu-id="fd4c8-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd4c8-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fd4c8-110">Child Elements</span></span>

<span data-ttu-id="fd4c8-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd4c8-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fd4c8-112">Parent Elements</span></span>

|<span data-ttu-id="fd4c8-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fd4c8-113">Element</span></span>|<span data-ttu-id="fd4c8-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="fd4c8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd4c8-115">Elemento TableColumnHeader para TableHeaders para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fd4c8-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="fd4c8-116">Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fd4c8-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fd4c8-117">Text Value</span></span>

<span data-ttu-id="fd4c8-118">Cuando sea posible, especifique un ancho (en caracteres) mayor que la longitud de los valores de propiedad mostrados.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd4c8-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fd4c8-119">Remarks</span></span>

<span data-ttu-id="fd4c8-120">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fd4c8-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd4c8-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fd4c8-121">Example</span></span>

<span data-ttu-id="fd4c8-122">En el ejemplo siguiente se muestra un elemento @no__t 0 cuyo ancho es de 16 caracteres.</span><span class="sxs-lookup"><span data-stu-id="fd4c8-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="fd4c8-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="fd4c8-123">See Also</span></span>

[<span data-ttu-id="fd4c8-124">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="fd4c8-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fd4c8-125">Elemento TableColumnHeader para TableHeader para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fd4c8-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="fd4c8-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd4c8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
