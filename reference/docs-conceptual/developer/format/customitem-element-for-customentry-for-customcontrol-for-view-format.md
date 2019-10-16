---
title: Elemento CustomItem para CustomEntry para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363954"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="433fc-102">Elemento CustomItem para CustomEntry for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="433fc-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="433fc-103">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="433fc-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="433fc-104">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="433fc-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="433fc-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="433fc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="433fc-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="433fc-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="433fc-107">Attributes and Elements</span></span>

<span data-ttu-id="433fc-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="433fc-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="433fc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="433fc-109">Attributes</span></span>

<span data-ttu-id="433fc-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="433fc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="433fc-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="433fc-111">Child Elements</span></span>

|<span data-ttu-id="433fc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="433fc-112">Element</span></span>|<span data-ttu-id="433fc-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="433fc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="433fc-114">Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="433fc-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="433fc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="433fc-116">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="433fc-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="433fc-117">Elemento Frame para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="433fc-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="433fc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="433fc-119">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="433fc-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="433fc-120">Elemento NewLine para CustomItem para el control personalizado de View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="433fc-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="433fc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="433fc-122">Agrega una línea en blanco a la presentación del control.</span><span class="sxs-lookup"><span data-stu-id="433fc-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="433fc-123">Elemento Text para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="433fc-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="433fc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="433fc-125">Especifica texto adicional para los datos mostrados por el control.</span><span class="sxs-lookup"><span data-stu-id="433fc-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="433fc-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="433fc-126">Parent Elements</span></span>

|<span data-ttu-id="433fc-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="433fc-127">Element</span></span>|<span data-ttu-id="433fc-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="433fc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="433fc-129">Elemento CustomEntry para CustomEntries para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="433fc-130">Proporciona una definición de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="433fc-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="433fc-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="433fc-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="433fc-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="433fc-132">See Also</span></span>

[<span data-ttu-id="433fc-133">Elemento CustomEntry para CustomEntries para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="433fc-134">Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="433fc-135">Elemento Frame para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="433fc-136">Elemento NewLine para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="433fc-137">Elemento Text para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="433fc-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="433fc-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="433fc-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
