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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363884"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="cb958-102">Elemento CustomItem para CustomEntry for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb958-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="cb958-103">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="cb958-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="cb958-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="cb958-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cb958-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb958-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cb958-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb958-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="cb958-107">Attributes and Elements</span></span>

<span data-ttu-id="cb958-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="cb958-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb958-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb958-109">Attributes</span></span>

<span data-ttu-id="cb958-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="cb958-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb958-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="cb958-111">Child Elements</span></span>

|<span data-ttu-id="cb958-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb958-112">Element</span></span>|<span data-ttu-id="cb958-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="cb958-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb958-114">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cb958-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb958-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cb958-116">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="cb958-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="cb958-117">Elemento Frame para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cb958-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb958-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cb958-119">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="cb958-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="cb958-120">Elemento NewLine para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cb958-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb958-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cb958-122">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="cb958-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="cb958-123">Elemento Text para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cb958-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb958-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cb958-125">Especifica texto adicional para los datos mostrados por el control.</span><span class="sxs-lookup"><span data-stu-id="cb958-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cb958-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="cb958-126">Parent Elements</span></span>

|<span data-ttu-id="cb958-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb958-127">Element</span></span>|<span data-ttu-id="cb958-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="cb958-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb958-129">Elemento CustomEntry para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="cb958-130">Proporciona una definición de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="cb958-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb958-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="cb958-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="cb958-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="cb958-132">See Also</span></span>

[<span data-ttu-id="cb958-133">Elemento CustomEntry para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="cb958-134">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="cb958-135">Elemento Frame para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="cb958-136">Elemento NewLine para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="cb958-137">Elemento Text para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb958-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="cb958-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb958-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
