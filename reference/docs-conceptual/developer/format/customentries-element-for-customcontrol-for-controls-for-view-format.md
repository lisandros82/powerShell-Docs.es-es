---
title: Elemento CustomEntries para CustomControl para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368814"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="9fb54-102">Elemento CustomEntries para CustomControl for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="9fb54-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="9fb54-103">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="9fb54-103">Provides the definitions for the control.</span></span> <span data-ttu-id="9fb54-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="9fb54-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9fb54-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9fb54-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9fb54-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9fb54-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fb54-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9fb54-107">Attributes and Elements</span></span>

<span data-ttu-id="9fb54-108">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="9fb54-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="9fb54-109">No hay ningún límite máximo para el número de elementos secundarios que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="9fb54-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fb54-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9fb54-110">Attributes</span></span>

<span data-ttu-id="9fb54-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9fb54-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9fb54-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9fb54-112">Child Elements</span></span>

|<span data-ttu-id="9fb54-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9fb54-113">Element</span></span>|<span data-ttu-id="9fb54-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="9fb54-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fb54-115">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9fb54-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="9fb54-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="9fb54-116">Required element.</span></span><br /><br /> <span data-ttu-id="9fb54-117">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="9fb54-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9fb54-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9fb54-118">Parent Elements</span></span>

|<span data-ttu-id="9fb54-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="9fb54-119">Element</span></span>|<span data-ttu-id="9fb54-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="9fb54-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fb54-121">Elemento CustomControl para el control de los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="9fb54-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="9fb54-122">Define el control utilizado por la vista.</span><span class="sxs-lookup"><span data-stu-id="9fb54-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9fb54-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9fb54-123">Remarks</span></span>

<span data-ttu-id="9fb54-124">En la mayoría de los casos, un control solo tiene una definición, que se especifica en un único elemento de `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="9fb54-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="9fb54-125">Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar objetos .NET diferentes.</span><span class="sxs-lookup"><span data-stu-id="9fb54-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="9fb54-126">En esos casos, puede definir un elemento `CustomEntry` para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="9fb54-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fb54-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="9fb54-127">See Also</span></span>

[<span data-ttu-id="9fb54-128">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9fb54-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="9fb54-129">Elemento CustomControl para el control de los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="9fb54-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="9fb54-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9fb54-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
