---
title: Elemento de marco para CustomItem para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859821"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="1dc95-102">Elemento Frame para CustomItem for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="1dc95-103">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="1dc95-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="1dc95-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="1dc95-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1dc95-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de marco de vista (formato) para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1dc95-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1dc95-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1dc95-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1dc95-107">Attributes and Elements</span></span>

<span data-ttu-id="1dc95-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="1dc95-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1dc95-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1dc95-109">Attributes</span></span>

<span data-ttu-id="1dc95-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1dc95-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1dc95-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1dc95-111">Child Elements</span></span>

|<span data-ttu-id="1dc95-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="1dc95-112">Element</span></span>|<span data-ttu-id="1dc95-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="1dc95-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="1dc95-114">Elemento necesario</span><span class="sxs-lookup"><span data-stu-id="1dc95-114">Required Element</span></span>|
|[<span data-ttu-id="1dc95-115">Elemento FirstLineHanging del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="1dc95-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1dc95-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1dc95-117">Especifica cuántos caracteres de la primera línea se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="1dc95-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="1dc95-118">Elemento FirstLineIndent del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="1dc95-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1dc95-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1dc95-120">Especifica cuántos caracteres de la primera línea se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="1dc95-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="1dc95-121">Elemento LeftIndent del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="1dc95-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1dc95-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1dc95-123">Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="1dc95-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="1dc95-124">Elemento RightIndent del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="1dc95-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1dc95-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1dc95-126">Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="1dc95-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1dc95-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1dc95-127">Parent Elements</span></span>

|<span data-ttu-id="1dc95-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1dc95-128">Element</span></span>|<span data-ttu-id="1dc95-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="1dc95-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1dc95-130">Elemento CustomItem para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="1dc95-131">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="1dc95-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1dc95-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1dc95-132">Remarks</span></span>

<span data-ttu-id="1dc95-133">No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementos en la misma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="1dc95-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dc95-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="1dc95-134">See Also</span></span>

[<span data-ttu-id="1dc95-135">Elemento FirstLineHanging del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="1dc95-136">Elemento FirstLineIndent del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="1dc95-137">Elemento LeftIndent del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="1dc95-138">Elemento RightIndent del marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="1dc95-139">Elemento CustomItem para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="1dc95-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="1dc95-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1dc95-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
