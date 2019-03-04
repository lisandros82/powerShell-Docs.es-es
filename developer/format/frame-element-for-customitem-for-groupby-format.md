---
title: Elemento de marco para CustomItem para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854851"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="28f55-102">Elemento Frame para CustomItem for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="28f55-103">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="28f55-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="28f55-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="28f55-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="28f55-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para elemento de marco de GroupBy (formato) de CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="28f55-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="28f55-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="28f55-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="28f55-107">Attributes and Elements</span></span>

<span data-ttu-id="28f55-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="28f55-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="28f55-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="28f55-109">Attributes</span></span>

<span data-ttu-id="28f55-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="28f55-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="28f55-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="28f55-111">Child Elements</span></span>

|<span data-ttu-id="28f55-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="28f55-112">Element</span></span>|<span data-ttu-id="28f55-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="28f55-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="28f55-114">Elemento necesario</span><span class="sxs-lookup"><span data-stu-id="28f55-114">Required Element</span></span>|
|[<span data-ttu-id="28f55-115">Elemento FirstLineHanging para marco de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="28f55-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="28f55-116">Optional element.</span></span><br /><br /> <span data-ttu-id="28f55-117">Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="28f55-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="28f55-118">Elemento FirstLineIndent marco para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="28f55-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="28f55-119">Optional element.</span></span><br /><br /> <span data-ttu-id="28f55-120">Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="28f55-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="28f55-121">Elemento LeftIndent marco para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="28f55-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="28f55-122">Optional element.</span></span><br /><br /> <span data-ttu-id="28f55-123">Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="28f55-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="28f55-124">[Elemento RightIndent marco para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento</span><span class="sxs-lookup"><span data-stu-id="28f55-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="28f55-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="28f55-125">Optional element.</span></span><br /><br /> <span data-ttu-id="28f55-126">Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="28f55-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="28f55-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="28f55-127">Parent Elements</span></span>

|<span data-ttu-id="28f55-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="28f55-128">Element</span></span>|<span data-ttu-id="28f55-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="28f55-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28f55-130">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="28f55-131">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="28f55-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="28f55-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="28f55-132">Remarks</span></span>

<span data-ttu-id="28f55-133">No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementos en la misma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="28f55-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="28f55-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="28f55-134">See Also</span></span>

[<span data-ttu-id="28f55-135">Elemento FirstLineHanging para marco de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="28f55-136">Elemento FirstLineIndent marco para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="28f55-137">Elemento LeftIndent marco para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="28f55-138">Elemento RightIndent marco para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="28f55-139">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="28f55-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="28f55-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="28f55-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
