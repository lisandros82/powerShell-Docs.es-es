---
title: Elemento CustomEntry para CustomEntries para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364054"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="01392-102">Elemento CustomEntry para CustomEntries for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="01392-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="01392-103">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="01392-103">Provides a definition of the control.</span></span> <span data-ttu-id="01392-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="01392-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="01392-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry View (Format) para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="01392-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="01392-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="01392-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01392-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="01392-107">Attributes and Elements</span></span>

<span data-ttu-id="01392-108">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="01392-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="01392-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="01392-109">Attributes</span></span>

<span data-ttu-id="01392-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="01392-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="01392-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="01392-111">Child Elements</span></span>

|<span data-ttu-id="01392-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="01392-112">Element</span></span>|<span data-ttu-id="01392-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="01392-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01392-114">Elemento EntrySelectedBy para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="01392-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="01392-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="01392-115">Optional element.</span></span><br /><br /> <span data-ttu-id="01392-116">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="01392-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="01392-117">Elemento CustomItem para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="01392-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="01392-118">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="01392-118">Required element.</span></span><br /><br /> <span data-ttu-id="01392-119">Define cómo el control muestra los datos.</span><span class="sxs-lookup"><span data-stu-id="01392-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="01392-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="01392-120">Parent Elements</span></span>

|<span data-ttu-id="01392-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="01392-121">Element</span></span>|<span data-ttu-id="01392-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="01392-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01392-123">Elemento CustomEntries para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="01392-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="01392-124">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="01392-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01392-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="01392-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="01392-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="01392-126">See Also</span></span>

[<span data-ttu-id="01392-127">Elemento CustomEntries para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="01392-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="01392-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="01392-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
