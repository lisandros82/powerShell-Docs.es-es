---
title: Elemento Frame para CustomItem para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363664"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="4c0ae-102">Elemento Frame para CustomItem for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4c0ae-103">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="4c0ae-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4c0ae-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para los controles de configuración (Format) elemento CustomItem para CustomEntry para controles para el elemento de marco de configuración para CustomItem para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c0ae-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4c0ae-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c0ae-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4c0ae-107">Attributes and Elements</span></span>

<span data-ttu-id="4c0ae-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c0ae-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4c0ae-109">Attributes</span></span>

<span data-ttu-id="4c0ae-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c0ae-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4c0ae-111">Child Elements</span></span>

|<span data-ttu-id="4c0ae-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4c0ae-112">Element</span></span>|<span data-ttu-id="4c0ae-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="4c0ae-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="4c0ae-114">Elemento obligatorio</span><span class="sxs-lookup"><span data-stu-id="4c0ae-114">Required Element</span></span>|
|[<span data-ttu-id="4c0ae-115">Elemento FirstLineHanging para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4c0ae-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4c0ae-117">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="4c0ae-118">Elemento FirstLineIndent para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4c0ae-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4c0ae-120">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="4c0ae-121">Elemento LeftIndent para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4c0ae-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4c0ae-123">Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="4c0ae-124">Elemento RightIndent para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4c0ae-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4c0ae-126">Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4c0ae-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4c0ae-127">Parent Elements</span></span>

|<span data-ttu-id="4c0ae-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="4c0ae-128">Element</span></span>|<span data-ttu-id="4c0ae-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="4c0ae-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c0ae-130">Elemento CustomItem de CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="4c0ae-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4c0ae-131">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4c0ae-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4c0ae-132">Remarks</span></span>

<span data-ttu-id="4c0ae-133">No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) en el mismo elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4c0ae-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c0ae-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="4c0ae-134">See Also</span></span>

[<span data-ttu-id="4c0ae-135">Elemento FirstLineHanging para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4c0ae-136">Elemento FirstLineIndent para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4c0ae-137">Elemento LeftIndent para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4c0ae-138">Elemento RightIndent para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4c0ae-139">Elemento CustomItem de CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="4c0ae-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4c0ae-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c0ae-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
