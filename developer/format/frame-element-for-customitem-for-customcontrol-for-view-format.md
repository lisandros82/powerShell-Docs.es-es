---
title: Elemento de marco para CustomItem para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054788"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="2274b-102">Elemento Frame para CustomItem for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="2274b-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="2274b-103">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="2274b-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="2274b-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="2274b-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2274b-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para elemento de marco de CustomControlView (formato) de CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2274b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2274b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2274b-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2274b-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2274b-107">Attributes and Elements</span></span>

<span data-ttu-id="2274b-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="2274b-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2274b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2274b-109">Attributes</span></span>

<span data-ttu-id="2274b-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2274b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2274b-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2274b-111">Child Elements</span></span>

|<span data-ttu-id="2274b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="2274b-112">Element</span></span>|<span data-ttu-id="2274b-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="2274b-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="2274b-114">Elemento necesario</span><span class="sxs-lookup"><span data-stu-id="2274b-114">Required Element</span></span>|
|[<span data-ttu-id="2274b-115">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="2274b-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2274b-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2274b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2274b-117">Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="2274b-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="2274b-118">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="2274b-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2274b-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2274b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2274b-120">Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="2274b-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="2274b-121">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="2274b-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2274b-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2274b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2274b-123">Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="2274b-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="2274b-124">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="2274b-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2274b-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2274b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2274b-126">Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="2274b-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2274b-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2274b-127">Parent Elements</span></span>

|<span data-ttu-id="2274b-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="2274b-128">Element</span></span>|<span data-ttu-id="2274b-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="2274b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2274b-130">Elemento CustomItem para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2274b-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="2274b-131">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="2274b-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2274b-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2274b-132">Remarks</span></span>

<span data-ttu-id="2274b-133">No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos en la misma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="2274b-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2274b-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="2274b-134">See Also</span></span>

[<span data-ttu-id="2274b-135">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="2274b-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2274b-136">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="2274b-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2274b-137">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="2274b-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2274b-138">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="2274b-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2274b-139">Elemento CustomItem para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2274b-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2274b-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2274b-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
