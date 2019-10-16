---
title: Elemento CustomEntries para CustomControl para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364094"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="17f0d-102">Elemento CustomEntries para CustomControl for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="17f0d-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="17f0d-103">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="17f0d-103">Provides the definitions for the control.</span></span> <span data-ttu-id="17f0d-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="17f0d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="17f0d-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="17f0d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17f0d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="17f0d-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17f0d-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="17f0d-107">Attributes and Elements</span></span>

<span data-ttu-id="17f0d-108">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="17f0d-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="17f0d-109">No hay ningún límite máximo para el número de elementos secundarios que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="17f0d-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="17f0d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="17f0d-110">Attributes</span></span>

<span data-ttu-id="17f0d-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="17f0d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17f0d-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="17f0d-112">Child Elements</span></span>

|<span data-ttu-id="17f0d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="17f0d-113">Element</span></span>|<span data-ttu-id="17f0d-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="17f0d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17f0d-115">Elemento CustomEntry para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="17f0d-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="17f0d-116">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="17f0d-116">Required element.</span></span><br /><br /> <span data-ttu-id="17f0d-117">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="17f0d-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="17f0d-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="17f0d-118">Parent Elements</span></span>

|<span data-ttu-id="17f0d-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="17f0d-119">Element</span></span>|<span data-ttu-id="17f0d-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="17f0d-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17f0d-121">Elemento CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="17f0d-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="17f0d-122">Define el control personalizado que muestra el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="17f0d-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="17f0d-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="17f0d-123">Remarks</span></span>

<span data-ttu-id="17f0d-124">En la mayoría de los casos, un control solo tiene una definición, que se especifica en un único elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="17f0d-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="17f0d-125">Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar grupos diferentes.</span><span class="sxs-lookup"><span data-stu-id="17f0d-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="17f0d-126">En esos casos, puede definir un elemento `CustomEntry` para un grupo.</span><span class="sxs-lookup"><span data-stu-id="17f0d-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="17f0d-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="17f0d-127">See Also</span></span>

[<span data-ttu-id="17f0d-128">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="17f0d-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="17f0d-129">Elemento CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="17f0d-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="17f0d-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="17f0d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
