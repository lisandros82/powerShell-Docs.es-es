---
title: Elemento Frame para CustomItem para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363654"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="8ea58-102">Elemento Frame para CustomItem for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="8ea58-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="8ea58-103">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="8ea58-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="8ea58-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="8ea58-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8ea58-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles de la vista (Format) elemento CustomItem de CustomEntry para los controles del elemento de marco View (Format) para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ea58-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8ea58-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ea58-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8ea58-107">Attributes and Elements</span></span>

<span data-ttu-id="8ea58-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="8ea58-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ea58-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8ea58-109">Attributes</span></span>

<span data-ttu-id="8ea58-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8ea58-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ea58-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8ea58-111">Child Elements</span></span>

|<span data-ttu-id="8ea58-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ea58-112">Element</span></span>|<span data-ttu-id="8ea58-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="8ea58-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="8ea58-114">Elemento obligatorio</span><span class="sxs-lookup"><span data-stu-id="8ea58-114">Required Element</span></span>|
|[<span data-ttu-id="8ea58-115">Elemento FirstLineHanging del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="8ea58-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8ea58-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8ea58-117">Especifica el número de caracteres que la primera línea se desplaza hacia la izquierda.</span><span class="sxs-lookup"><span data-stu-id="8ea58-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="8ea58-118">Elemento FirstLineIndent del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="8ea58-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8ea58-119">Optional element.</span></span><br /><br /> <span data-ttu-id="8ea58-120">Especifica el número de caracteres que la primera línea se desplaza hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="8ea58-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="8ea58-121">Elemento LeftIndent del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="8ea58-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8ea58-122">Optional element.</span></span><br /><br /> <span data-ttu-id="8ea58-123">Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="8ea58-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="8ea58-124">Elemento RightIndent del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="8ea58-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8ea58-125">Optional element.</span></span><br /><br /> <span data-ttu-id="8ea58-126">Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="8ea58-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8ea58-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8ea58-127">Parent Elements</span></span>

|<span data-ttu-id="8ea58-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="8ea58-128">Element</span></span>|<span data-ttu-id="8ea58-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="8ea58-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ea58-130">Elemento CustomItem para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8ea58-131">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="8ea58-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ea58-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8ea58-132">Remarks</span></span>

<span data-ttu-id="8ea58-133">No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) en el mismo elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="8ea58-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ea58-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="8ea58-134">See Also</span></span>

[<span data-ttu-id="8ea58-135">Elemento FirstLineHanging del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="8ea58-136">Elemento FirstLineIndent del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="8ea58-137">Elemento LeftIndent del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="8ea58-138">Elemento RightIndent del marco de controles de la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="8ea58-139">Elemento CustomItem para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="8ea58-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8ea58-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ea58-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
