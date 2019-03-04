---
title: Elemento Alignment para TableColumnItem para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858211"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="fe44b-102">Elemento Alignment para TableColumnItem for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fe44b-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="fe44b-103">Define cómo se muestran los datos en una columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="fe44b-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="fe44b-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento de configuración (formato) Elemento Alignment para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="fe44b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe44b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fe44b-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe44b-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fe44b-106">Attributes and Elements</span></span>

<span data-ttu-id="fe44b-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `Alignment` elemento.</span><span class="sxs-lookup"><span data-stu-id="fe44b-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe44b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe44b-108">Attributes</span></span>

<span data-ttu-id="fe44b-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fe44b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe44b-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fe44b-110">Child Elements</span></span>

<span data-ttu-id="fe44b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fe44b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe44b-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fe44b-112">Parent Elements</span></span>

|<span data-ttu-id="fe44b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe44b-113">Element</span></span>|<span data-ttu-id="fe44b-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="fe44b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe44b-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="fe44b-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="fe44b-116">Define una etiqueta, el ancho y la alineación de los datos de una columna de la tabla.</span><span class="sxs-lookup"><span data-stu-id="fe44b-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe44b-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fe44b-117">Text Value</span></span>

<span data-ttu-id="fe44b-118">Especifique uno de los siguientes valores.</span><span class="sxs-lookup"><span data-stu-id="fe44b-118">Specify one of the following values.</span></span> <span data-ttu-id="fe44b-119">(Estos valores no distinguen entre mayúsculas y minúsculas).</span><span class="sxs-lookup"><span data-stu-id="fe44b-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="fe44b-120">Desplazamientos a la izquierda los datos mostrados en la columna a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="fe44b-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="fe44b-121">(Este es el valor predeterminado si no se especifica este elemento).</span><span class="sxs-lookup"><span data-stu-id="fe44b-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="fe44b-122">Desplazamientos a la derecha los datos mostrados en la columna a la derecha.</span><span class="sxs-lookup"><span data-stu-id="fe44b-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="fe44b-123">Centros de centro de los datos mostrados en la columna.</span><span class="sxs-lookup"><span data-stu-id="fe44b-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe44b-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fe44b-124">Remarks</span></span>

<span data-ttu-id="fe44b-125">Para obtener más información acerca de los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fe44b-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe44b-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="fe44b-126">See Also</span></span>

[<span data-ttu-id="fe44b-127">Vista de tabla</span><span class="sxs-lookup"><span data-stu-id="fe44b-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fe44b-128">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="fe44b-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
