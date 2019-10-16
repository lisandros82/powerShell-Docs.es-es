---
title: Elemento CustomEntry para CustomEntries para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364024"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="1ce0a-102">Elemento CustomEntry para CustomEntries for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="1ce0a-103">Proporciona una definición de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="1ce0a-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ce0a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1ce0a-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ce0a-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1ce0a-106">Attributes and Elements</span></span>

<span data-ttu-id="1ce0a-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="1ce0a-108">Debe especificar los elementos que se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ce0a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ce0a-109">Attributes</span></span>

<span data-ttu-id="1ce0a-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ce0a-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1ce0a-111">Child Elements</span></span>

|<span data-ttu-id="1ce0a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ce0a-112">Element</span></span>|<span data-ttu-id="1ce0a-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="1ce0a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ce0a-114">Elemento EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1ce0a-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1ce0a-116">Define los tipos .NET que usan la definición de la vista de control personalizada o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="1ce0a-117">Elemento CustomItem para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1ce0a-118">Define un control para la definición del control personalizado.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1ce0a-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1ce0a-119">Parent Elements</span></span>

|<span data-ttu-id="1ce0a-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ce0a-120">Element</span></span>|<span data-ttu-id="1ce0a-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="1ce0a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ce0a-122">Elemento CustomEntries para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="1ce0a-123">Proporciona las definiciones de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="1ce0a-124">La vista de control personalizada debe especificar una o más definiciones.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1ce0a-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1ce0a-125">Remarks</span></span>

<span data-ttu-id="1ce0a-126">En la mayoría de los casos, solo se requiere una definición para cada vista de control personalizada, pero es posible tener varias definiciones si se desea usar la misma vista para mostrar diferentes objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="1ce0a-127">En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="1ce0a-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ce0a-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="1ce0a-128">See Also</span></span>

[<span data-ttu-id="1ce0a-129">Elemento CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="1ce0a-130">Elemento CustomItem para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1ce0a-131">Elemento EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="1ce0a-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1ce0a-132">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ce0a-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
