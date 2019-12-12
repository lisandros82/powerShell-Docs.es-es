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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363944"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="506c2-102">Elemento CustomItem para CustomEntry for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="506c2-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="506c2-103">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="506c2-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="506c2-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="506c2-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="506c2-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para controles para el elemento CustomItem View (Format) para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="506c2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="506c2-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="506c2-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="506c2-107">Attributes and Elements</span></span>

<span data-ttu-id="506c2-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="506c2-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="506c2-109">Para obtener más información, vea Comentarios.</span><span class="sxs-lookup"><span data-stu-id="506c2-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="506c2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="506c2-110">Attributes</span></span>

<span data-ttu-id="506c2-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="506c2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="506c2-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="506c2-112">Child Elements</span></span>

|<span data-ttu-id="506c2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="506c2-113">Element</span></span>|<span data-ttu-id="506c2-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="506c2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="506c2-115">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="506c2-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="506c2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="506c2-117">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="506c2-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="506c2-118">Elemento Frame para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="506c2-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="506c2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="506c2-120">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="506c2-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="506c2-121">Elemento NewLine para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="506c2-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="506c2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="506c2-123">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="506c2-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="506c2-124">Elemento Text para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="506c2-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="506c2-125">Optional element.</span></span><br /><br /> <span data-ttu-id="506c2-126">Agrega texto, como paréntesis o corchetes, a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="506c2-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="506c2-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="506c2-127">Parent Elements</span></span>

|<span data-ttu-id="506c2-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="506c2-128">Element</span></span>|<span data-ttu-id="506c2-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="506c2-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="506c2-130">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="506c2-131">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="506c2-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="506c2-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="506c2-132">Remarks</span></span>

<span data-ttu-id="506c2-133">Al especificar los elementos secundarios del elemento `CustomItem`, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="506c2-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="506c2-134">Los elementos secundarios se deben agregar en la secuencia siguiente: `ExpressionBinding`, `NewLine`, `Text`y `Frame`.</span><span class="sxs-lookup"><span data-stu-id="506c2-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="506c2-135">No hay ningún límite máximo en el número de secuencias que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="506c2-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="506c2-136">En cada secuencia, no hay ningún límite máximo para el número de elementos `ExpressionBinding` que puede usar.</span><span class="sxs-lookup"><span data-stu-id="506c2-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="506c2-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="506c2-137">See Also</span></span>

[<span data-ttu-id="506c2-138">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="506c2-139">Elemento Frame para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="506c2-140">Elemento NewLine para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="506c2-141">Elemento Text para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="506c2-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="506c2-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="506c2-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
