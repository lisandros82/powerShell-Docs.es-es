---
title: Elemento CustomItem para CustomEntry para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363884"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="67081-102">Elemento CustomItem para CustomEntry for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="67081-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="67081-103">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="67081-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="67081-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="67081-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="67081-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67081-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="67081-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67081-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="67081-107">Attributes and Elements</span></span>

<span data-ttu-id="67081-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="67081-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67081-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="67081-109">Attributes</span></span>

<span data-ttu-id="67081-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="67081-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67081-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="67081-111">Child Elements</span></span>

|<span data-ttu-id="67081-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="67081-112">Element</span></span>|<span data-ttu-id="67081-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="67081-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67081-114">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="67081-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67081-115">Optional element.</span></span><br /><br /> <span data-ttu-id="67081-116">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="67081-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="67081-117">Elemento Frame para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="67081-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67081-118">Optional element.</span></span><br /><br /> <span data-ttu-id="67081-119">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="67081-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="67081-120">Elemento NewLine para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="67081-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67081-121">Optional element.</span></span><br /><br /> <span data-ttu-id="67081-122">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="67081-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="67081-123">Elemento Text para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="67081-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67081-124">Optional element.</span></span><br /><br /> <span data-ttu-id="67081-125">Especifica texto adicional para los datos mostrados por el control.</span><span class="sxs-lookup"><span data-stu-id="67081-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67081-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="67081-126">Parent Elements</span></span>

|<span data-ttu-id="67081-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="67081-127">Element</span></span>|<span data-ttu-id="67081-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="67081-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67081-129">Elemento CustomEntry para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="67081-130">Proporciona una definición de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="67081-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67081-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="67081-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="67081-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="67081-132">See Also</span></span>

[<span data-ttu-id="67081-133">Elemento CustomEntry para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="67081-134">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="67081-135">Elemento Frame para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="67081-136">Elemento NewLine para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="67081-137">Elemento Text para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67081-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="67081-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="67081-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
