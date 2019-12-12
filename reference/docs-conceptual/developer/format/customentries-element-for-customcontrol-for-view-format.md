---
title: Elemento CustomEntries para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364084"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="a8934-102">Elemento CustomEntries para CustomControl for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a8934-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="a8934-103">Proporciona las definiciones de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="a8934-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="a8934-104">La vista de control personalizada debe especificar una o más definiciones.</span><span class="sxs-lookup"><span data-stu-id="a8934-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="a8934-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8934-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8934-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a8934-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8934-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="a8934-107">Attributes and Elements</span></span>

<span data-ttu-id="a8934-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomControlEntries`.</span><span class="sxs-lookup"><span data-stu-id="a8934-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="a8934-109">Debe especificar uno o varios elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="a8934-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8934-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8934-110">Attributes</span></span>

<span data-ttu-id="a8934-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="a8934-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8934-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="a8934-112">Child Elements</span></span>

|<span data-ttu-id="a8934-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8934-113">Element</span></span>|<span data-ttu-id="a8934-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="a8934-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8934-115">Elemento CustomEntry para CustomEntries para View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8934-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="a8934-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="a8934-116">Required element.</span></span><br /><br /> <span data-ttu-id="a8934-117">Proporciona una definición de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="a8934-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a8934-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="a8934-118">Parent Elements</span></span>

|<span data-ttu-id="a8934-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8934-119">Element</span></span>|<span data-ttu-id="a8934-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="a8934-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8934-121">Elemento CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8934-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="a8934-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="a8934-122">Required element.</span></span><br /><br /> <span data-ttu-id="a8934-123">Define un formato de control personalizado para la vista.</span><span class="sxs-lookup"><span data-stu-id="a8934-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a8934-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a8934-124">Remarks</span></span>

<span data-ttu-id="a8934-125">En la mayoría de los casos, un control solo tiene una definición, que se define en un único elemento de `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="a8934-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="a8934-126">Sin embargo, es posible tener varias definiciones si desea utilizar el mismo control para mostrar objetos .NET diferentes.</span><span class="sxs-lookup"><span data-stu-id="a8934-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="a8934-127">En esos casos, puede definir un elemento `CustomEntry` para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="a8934-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8934-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="a8934-128">See Also</span></span>

[<span data-ttu-id="a8934-129">Elemento CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8934-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="a8934-130">Elemento CustomEntry para CustomEntries para View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8934-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a8934-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8934-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
