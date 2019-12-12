---
title: Elemento Frame para CustomItem para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363644"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="42018-102">Elemento Frame para CustomItem for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="42018-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="42018-103">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="42018-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="42018-104">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="42018-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="42018-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para CustomControlView (Format) elemento Frame para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="42018-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42018-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="42018-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42018-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="42018-107">Attributes and Elements</span></span>

<span data-ttu-id="42018-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="42018-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42018-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="42018-109">Attributes</span></span>

<span data-ttu-id="42018-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="42018-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42018-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="42018-111">Child Elements</span></span>

|<span data-ttu-id="42018-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="42018-112">Element</span></span>|<span data-ttu-id="42018-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="42018-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="42018-114">Elemento obligatorio</span><span class="sxs-lookup"><span data-stu-id="42018-114">Required Element</span></span>|
|[<span data-ttu-id="42018-115">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="42018-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="42018-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42018-116">Optional element.</span></span><br /><br /> <span data-ttu-id="42018-117">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda.</span><span class="sxs-lookup"><span data-stu-id="42018-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="42018-118">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="42018-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="42018-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42018-119">Optional element.</span></span><br /><br /> <span data-ttu-id="42018-120">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="42018-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="42018-121">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="42018-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="42018-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42018-122">Optional element.</span></span><br /><br /> <span data-ttu-id="42018-123">Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="42018-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="42018-124">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="42018-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="42018-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="42018-125">Optional element.</span></span><br /><br /> <span data-ttu-id="42018-126">Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="42018-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42018-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="42018-127">Parent Elements</span></span>

|<span data-ttu-id="42018-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="42018-128">Element</span></span>|<span data-ttu-id="42018-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="42018-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42018-130">Elemento CustomItem para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="42018-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="42018-131">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="42018-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42018-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="42018-132">Remarks</span></span>

<span data-ttu-id="42018-133">No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) en el mismo elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="42018-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="42018-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="42018-134">See Also</span></span>

[<span data-ttu-id="42018-135">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="42018-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42018-136">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="42018-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42018-137">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="42018-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42018-138">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="42018-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42018-139">Elemento CustomItem para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="42018-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42018-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42018-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
