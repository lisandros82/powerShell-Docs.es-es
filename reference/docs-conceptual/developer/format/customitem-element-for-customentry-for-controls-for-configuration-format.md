---
title: Elemento CustomItem para CustomEntry para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364034"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="11b60-102">Elemento CustomItem para CustomEntry for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="11b60-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="11b60-103">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="11b60-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="11b60-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="11b60-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="11b60-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento CustomItem para CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="11b60-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="11b60-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="11b60-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11b60-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="11b60-107">Attributes and Elements</span></span>

<span data-ttu-id="11b60-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="11b60-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="11b60-109">Para obtener más información, vea Comentarios.</span><span class="sxs-lookup"><span data-stu-id="11b60-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="11b60-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="11b60-110">Attributes</span></span>

<span data-ttu-id="11b60-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="11b60-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11b60-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="11b60-112">Child Elements</span></span>

|<span data-ttu-id="11b60-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="11b60-113">Element</span></span>|<span data-ttu-id="11b60-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="11b60-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11b60-115">Elemento ExpressionBinding de CustomItem para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="11b60-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="11b60-116">Optional element.</span></span><br /><br /> <span data-ttu-id="11b60-117">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="11b60-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="11b60-118">Elemento Frame para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="11b60-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="11b60-119">Optional element.</span></span><br /><br /> <span data-ttu-id="11b60-120">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="11b60-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="11b60-121">Elemento NewLine para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="11b60-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="11b60-122">Optional element.</span></span><br /><br /> <span data-ttu-id="11b60-123">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="11b60-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="11b60-124">Elemento de texto para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="11b60-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="11b60-125">Optional element.</span></span><br /><br /> <span data-ttu-id="11b60-126">Agrega texto, como paréntesis o corchetes, a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="11b60-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11b60-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="11b60-127">Parent Elements</span></span>

|<span data-ttu-id="11b60-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="11b60-128">Element</span></span>|<span data-ttu-id="11b60-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="11b60-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11b60-130">Elemento CustomEntry para CustomControl para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="11b60-131">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="11b60-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11b60-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="11b60-132">Remarks</span></span>

<span data-ttu-id="11b60-133">Al especificar los elementos secundarios del elemento `CustomItem`, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="11b60-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="11b60-134">Los elementos secundarios se deben agregar en la secuencia siguiente: `ExpressionBinding`, `NewLine`, `Text`y `Frame`.</span><span class="sxs-lookup"><span data-stu-id="11b60-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="11b60-135">No hay ningún límite máximo en el número de secuencias que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="11b60-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="11b60-136">En cada secuencia, no hay ningún límite máximo para el número de elementos `ExpressionBinding` que puede usar.</span><span class="sxs-lookup"><span data-stu-id="11b60-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="11b60-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="11b60-137">See Also</span></span>

[<span data-ttu-id="11b60-138">Elemento ExpressionBinding de CustomItem para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="11b60-139">Elemento Frame para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="11b60-140">Elemento NewLine para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="11b60-141">Elemento de texto para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="11b60-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="11b60-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="11b60-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
