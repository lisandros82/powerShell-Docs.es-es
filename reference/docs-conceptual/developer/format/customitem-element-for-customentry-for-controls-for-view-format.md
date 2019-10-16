---
title: Elemento CustomItem para CustomEntry para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363944"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="b6e9a-102">Elemento CustomItem para CustomEntry for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="b6e9a-103">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="b6e9a-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b6e9a-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para controles para el elemento CustomItem View (Format) para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6e9a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b6e9a-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6e9a-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b6e9a-107">Attributes and Elements</span></span>

<span data-ttu-id="b6e9a-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="b6e9a-109">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6e9a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6e9a-110">Attributes</span></span>

<span data-ttu-id="b6e9a-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6e9a-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b6e9a-112">Child Elements</span></span>

|<span data-ttu-id="b6e9a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6e9a-113">Element</span></span>|<span data-ttu-id="b6e9a-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="b6e9a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6e9a-115">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b6e9a-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b6e9a-117">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b6e9a-118">Elemento Frame para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b6e9a-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b6e9a-120">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="b6e9a-121">Elemento NewLine para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b6e9a-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b6e9a-123">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b6e9a-124">Elemento Text para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b6e9a-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b6e9a-126">Agrega texto, como paréntesis o corchetes, a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b6e9a-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b6e9a-127">Parent Elements</span></span>

|<span data-ttu-id="b6e9a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6e9a-128">Element</span></span>|<span data-ttu-id="b6e9a-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="b6e9a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6e9a-130">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b6e9a-131">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b6e9a-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b6e9a-132">Remarks</span></span>

<span data-ttu-id="b6e9a-133">Al especificar los elementos secundarios del elemento `CustomItem`, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b6e9a-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="b6e9a-134">Los elementos secundarios deben agregarse en la secuencia siguiente: `ExpressionBinding`, `NewLine`, `Text` y `Frame`.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="b6e9a-135">No hay ningún límite máximo en el número de secuencias que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="b6e9a-136">En cada secuencia, no hay ningún límite máximo para el número de elementos `ExpressionBinding` que puede usar.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6e9a-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="b6e9a-137">See Also</span></span>

[<span data-ttu-id="b6e9a-138">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b6e9a-139">Elemento Frame para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b6e9a-140">Elemento NewLine para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b6e9a-141">Elemento Text para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b6e9a-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6e9a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
