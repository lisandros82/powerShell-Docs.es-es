---
title: Elemento ColumnNumber para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364224"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="3123f-102">Elemento ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3123f-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="3123f-103">Especifica el número de columnas que se muestran en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="3123f-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="3123f-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento ColumnNumber para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3123f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3123f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3123f-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3123f-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3123f-106">Attributes and Elements</span></span>

<span data-ttu-id="3123f-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ColumnNumber`.</span><span class="sxs-lookup"><span data-stu-id="3123f-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3123f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3123f-108">Attributes</span></span>

<span data-ttu-id="3123f-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3123f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3123f-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3123f-110">Child Elements</span></span>

<span data-ttu-id="3123f-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3123f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3123f-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3123f-112">Parent Elements</span></span>

|<span data-ttu-id="3123f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3123f-113">Element</span></span>|<span data-ttu-id="3123f-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="3123f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3123f-115">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3123f-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="3123f-116">Define un formato de lista ancho (valor único) para la vista.</span><span class="sxs-lookup"><span data-stu-id="3123f-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3123f-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3123f-117">Text Value</span></span>

<span data-ttu-id="3123f-118">Especifique un valor entero positivo.</span><span class="sxs-lookup"><span data-stu-id="3123f-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="3123f-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3123f-119">Remarks</span></span>

<span data-ttu-id="3123f-120">Al definir una vista ampliada, puede Agregar el elemento `AutoSize` o el elemento `ColumnNumber`, pero no puede Agregar ambos.</span><span class="sxs-lookup"><span data-stu-id="3123f-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="3123f-121">Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3123f-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="3123f-122">Para obtener un ejemplo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3123f-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3123f-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="3123f-123">See Also</span></span>

[<span data-ttu-id="3123f-124">AutoSize (elemento) para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3123f-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="3123f-125">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="3123f-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3123f-126">Vista amplia (básica)</span><span class="sxs-lookup"><span data-stu-id="3123f-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="3123f-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3123f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
