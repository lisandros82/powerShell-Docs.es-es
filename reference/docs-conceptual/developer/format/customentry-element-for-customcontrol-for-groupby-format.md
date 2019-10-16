---
title: Elemento CustomEntry para CustomControl para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364064"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="a1b47-102">Elemento CustomEntry para CustomControl for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a1b47-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="a1b47-103">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="a1b47-103">Provides a definition of the control.</span></span> <span data-ttu-id="a1b47-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="a1b47-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a1b47-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1b47-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a1b47-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1b47-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="a1b47-107">Attributes and Elements</span></span>

<span data-ttu-id="a1b47-108">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="a1b47-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1b47-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1b47-109">Attributes</span></span>

<span data-ttu-id="a1b47-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="a1b47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1b47-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="a1b47-111">Child Elements</span></span>

|<span data-ttu-id="a1b47-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1b47-112">Element</span></span>|<span data-ttu-id="a1b47-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="a1b47-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1b47-114">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a1b47-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a1b47-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b47-116">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="a1b47-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a1b47-117">Elemento CustomItem para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a1b47-118">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="a1b47-118">Required element.</span></span><br /><br /> <span data-ttu-id="a1b47-119">Define cómo el control muestra los datos.</span><span class="sxs-lookup"><span data-stu-id="a1b47-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1b47-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="a1b47-120">Parent Elements</span></span>

|<span data-ttu-id="a1b47-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1b47-121">Element</span></span>|<span data-ttu-id="a1b47-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="a1b47-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1b47-123">Elemento CustomEntries para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="a1b47-124">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="a1b47-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1b47-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a1b47-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a1b47-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="a1b47-126">See Also</span></span>

[<span data-ttu-id="a1b47-127">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a1b47-128">Elemento CustomItem para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a1b47-129">Elemento CustomEntries para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a1b47-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="a1b47-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1b47-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
