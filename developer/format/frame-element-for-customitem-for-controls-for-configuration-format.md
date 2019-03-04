---
title: Elemento de marco para CustomItem para los controles para la configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862981"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="009dd-102">Elemento Frame para CustomItem for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="009dd-103">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="009dd-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="009dd-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="009dd-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="009dd-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de marco de configuración para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="009dd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="009dd-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="009dd-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="009dd-107">Attributes and Elements</span></span>

<span data-ttu-id="009dd-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="009dd-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="009dd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="009dd-109">Attributes</span></span>

<span data-ttu-id="009dd-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="009dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="009dd-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="009dd-111">Child Elements</span></span>

|<span data-ttu-id="009dd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="009dd-112">Element</span></span>|<span data-ttu-id="009dd-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="009dd-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="009dd-114">Elemento necesario</span><span class="sxs-lookup"><span data-stu-id="009dd-114">Required Element</span></span>|
|[<span data-ttu-id="009dd-115">Elemento FirstLineHanging marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="009dd-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="009dd-116">Optional element.</span></span><br /><br /> <span data-ttu-id="009dd-117">Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="009dd-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="009dd-118">Elemento FirstLineIndent marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="009dd-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="009dd-119">Optional element.</span></span><br /><br /> <span data-ttu-id="009dd-120">Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="009dd-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="009dd-121">Elemento LeftIndent marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="009dd-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="009dd-122">Optional element.</span></span><br /><br /> <span data-ttu-id="009dd-123">Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="009dd-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="009dd-124">Elemento RightIndent marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="009dd-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="009dd-125">Optional element.</span></span><br /><br /> <span data-ttu-id="009dd-126">Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="009dd-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="009dd-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="009dd-127">Parent Elements</span></span>

|<span data-ttu-id="009dd-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="009dd-128">Element</span></span>|<span data-ttu-id="009dd-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="009dd-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="009dd-130">Elemento CustomItem para CustomEntry para los controles de configuración</span><span class="sxs-lookup"><span data-stu-id="009dd-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="009dd-131">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="009dd-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="009dd-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="009dd-132">Remarks</span></span>

<span data-ttu-id="009dd-133">No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos en la misma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="009dd-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="009dd-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="009dd-134">See Also</span></span>

[<span data-ttu-id="009dd-135">Elemento FirstLineHanging marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="009dd-136">Elemento FirstLineIndent marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="009dd-137">Elemento LeftIndent marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="009dd-138">Elemento RightIndent marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="009dd-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="009dd-139">Elemento CustomItem para CustomEntry para los controles de configuración</span><span class="sxs-lookup"><span data-stu-id="009dd-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="009dd-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="009dd-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
