---
title: Elemento CustomEntries para CustomControl para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368824"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="b20f3-102">Elemento CustomEntries para CustomControl for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="b20f3-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b20f3-103">Proporciona las definiciones de un control común.</span><span class="sxs-lookup"><span data-stu-id="b20f3-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="b20f3-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="b20f3-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b20f3-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Aplique</span><span class="sxs-lookup"><span data-stu-id="b20f3-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b20f3-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b20f3-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b20f3-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b20f3-107">Attributes and Elements</span></span>

<span data-ttu-id="b20f3-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomEntries`.</span><span class="sxs-lookup"><span data-stu-id="b20f3-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="b20f3-109">Debe especificar uno o varios elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="b20f3-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b20f3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b20f3-110">Attributes</span></span>

<span data-ttu-id="b20f3-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b20f3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b20f3-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b20f3-112">Child Elements</span></span>

|<span data-ttu-id="b20f3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b20f3-113">Element</span></span>|<span data-ttu-id="b20f3-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="b20f3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b20f3-115">Elemento CustomEntry para CustomControl para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="b20f3-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="b20f3-116">Proporciona una definición del control común.</span><span class="sxs-lookup"><span data-stu-id="b20f3-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b20f3-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b20f3-117">Parent Elements</span></span>

|<span data-ttu-id="b20f3-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b20f3-118">Element</span></span>|<span data-ttu-id="b20f3-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="b20f3-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b20f3-120">Elemento CustomControl para el control de la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="b20f3-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="b20f3-121">Define un control común.</span><span class="sxs-lookup"><span data-stu-id="b20f3-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b20f3-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b20f3-122">Remarks</span></span>

<span data-ttu-id="b20f3-123">En la mayoría de los casos, un control solo tiene una definición, que se define en un único elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="b20f3-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="b20f3-124">Sin embargo, es posible tener varias definiciones si desea utilizar el mismo control para mostrar objetos .NET diferentes.</span><span class="sxs-lookup"><span data-stu-id="b20f3-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="b20f3-125">En esos casos, puede definir un elemento `CustomEntry` para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="b20f3-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b20f3-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="b20f3-126">See Also</span></span>

[<span data-ttu-id="b20f3-127">Elemento CustomControl para el control de la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="b20f3-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b20f3-128">Elemento CustomEntry para CustomControl para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="b20f3-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="b20f3-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b20f3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
