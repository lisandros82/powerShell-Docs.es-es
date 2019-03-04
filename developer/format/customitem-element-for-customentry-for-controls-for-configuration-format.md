---
title: Elemento CustomItem para CustomEntry para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862941"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="42d32-102">Elemento CustomItem para CustomEntry for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="42d32-103">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="42d32-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="42d32-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="42d32-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="42d32-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de configuración</span><span class="sxs-lookup"><span data-stu-id="42d32-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="42d32-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="42d32-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42d32-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="42d32-107">Attributes and Elements</span></span>

<span data-ttu-id="42d32-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="42d32-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="42d32-109">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="42d32-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="42d32-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="42d32-110">Attributes</span></span>

<span data-ttu-id="42d32-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="42d32-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42d32-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="42d32-112">Child Elements</span></span>

|<span data-ttu-id="42d32-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="42d32-113">Element</span></span>|<span data-ttu-id="42d32-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="42d32-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42d32-115">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="42d32-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42d32-116">Optional element.</span></span><br /><br /> <span data-ttu-id="42d32-117">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="42d32-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="42d32-118">Elemento de marco para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="42d32-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42d32-119">Optional element.</span></span><br /><br /> <span data-ttu-id="42d32-120">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="42d32-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="42d32-121">Elemento de nueva línea para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="42d32-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42d32-122">Optional element.</span></span><br /><br /> <span data-ttu-id="42d32-123">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="42d32-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="42d32-124">Elemento de texto para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="42d32-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42d32-125">Optional element.</span></span><br /><br /> <span data-ttu-id="42d32-126">Agrega texto, como paréntesis o corchetes, a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="42d32-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42d32-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="42d32-127">Parent Elements</span></span>

|<span data-ttu-id="42d32-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="42d32-128">Element</span></span>|<span data-ttu-id="42d32-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="42d32-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42d32-130">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="42d32-131">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="42d32-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42d32-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="42d32-132">Remarks</span></span>

<span data-ttu-id="42d32-133">Al especificar los elementos secundarios de la `CustomItem` elemento, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="42d32-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="42d32-134">Deben agregarse los elementos secundarios en la siguiente secuencia: `ExpressionBinding`, `NewLine`, `Text`, y `Frame`.</span><span class="sxs-lookup"><span data-stu-id="42d32-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="42d32-135">No hay ningún límite máximo para el número de secuencias que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="42d32-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="42d32-136">En cada secuencia, no hay ningún límite máximo para el número de `ExpressionBinding` elementos que se pueden usar.</span><span class="sxs-lookup"><span data-stu-id="42d32-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="42d32-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="42d32-137">See Also</span></span>

[<span data-ttu-id="42d32-138">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="42d32-139">Elemento de marco para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="42d32-140">Elemento de nueva línea para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="42d32-141">Elemento de texto para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="42d32-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="42d32-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42d32-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
