---
title: Elemento Frame para CustomItem para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362954"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="badb1-102">Elemento Frame para CustomItem for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="badb1-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="badb1-103">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="badb1-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="badb1-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="badb1-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="badb1-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para el elemento de marco GroupBy (Format) para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="badb1-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="badb1-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="badb1-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="badb1-107">Attributes and Elements</span></span>

<span data-ttu-id="badb1-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="badb1-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="badb1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="badb1-109">Attributes</span></span>

<span data-ttu-id="badb1-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="badb1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="badb1-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="badb1-111">Child Elements</span></span>

|<span data-ttu-id="badb1-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="badb1-112">Element</span></span>|<span data-ttu-id="badb1-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="badb1-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="badb1-114">Elemento obligatorio</span><span class="sxs-lookup"><span data-stu-id="badb1-114">Required Element</span></span>|
|[<span data-ttu-id="badb1-115">Elemento FirstLineHanging para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="badb1-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="badb1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="badb1-117">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la izquierda.</span><span class="sxs-lookup"><span data-stu-id="badb1-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="badb1-118">Elemento FirstLineIndent para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="badb1-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="badb1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="badb1-120">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="badb1-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="badb1-121">Elemento LeftIndent para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="badb1-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="badb1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="badb1-123">Especifica el número de caracteres que los datos se desplazan fuera del margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="badb1-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="badb1-124">[Elemento RightIndent para Frame para GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="badb1-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="badb1-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="badb1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="badb1-126">Especifica el número de caracteres que los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="badb1-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="badb1-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="badb1-127">Parent Elements</span></span>

|<span data-ttu-id="badb1-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="badb1-128">Element</span></span>|<span data-ttu-id="badb1-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="badb1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="badb1-130">Elemento CustomItem para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="badb1-131">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="badb1-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="badb1-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="badb1-132">Remarks</span></span>

<span data-ttu-id="badb1-133">No se pueden especificar los elementos [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) en el mismo elemento `Frame`.</span><span class="sxs-lookup"><span data-stu-id="badb1-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="badb1-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="badb1-134">See Also</span></span>

[<span data-ttu-id="badb1-135">Elemento FirstLineHanging para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="badb1-136">Elemento FirstLineIndent para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="badb1-137">Elemento LeftIndent para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="badb1-138">Elemento RightIndent para Frame para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="badb1-139">Elemento CustomItem para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="badb1-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="badb1-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="badb1-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
