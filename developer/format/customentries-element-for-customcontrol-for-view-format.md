---
title: Elemento CustomEntries para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861701"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="2c1db-102">Elemento CustomEntries para CustomControl for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2c1db-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="2c1db-103">Proporciona las definiciones de la vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="2c1db-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="2c1db-104">La vista de control personalizado debe especificar una o varias definiciones.</span><span class="sxs-lookup"><span data-stu-id="2c1db-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="2c1db-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2c1db-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c1db-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2c1db-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c1db-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2c1db-107">Attributes and Elements</span></span>

<span data-ttu-id="2c1db-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="2c1db-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="2c1db-109">Debe especificar uno o más elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="2c1db-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c1db-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2c1db-110">Attributes</span></span>

<span data-ttu-id="2c1db-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2c1db-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c1db-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2c1db-112">Child Elements</span></span>

|<span data-ttu-id="2c1db-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c1db-113">Element</span></span>|<span data-ttu-id="2c1db-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="2c1db-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c1db-115">Elemento CustomEntry para CustomEntries para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2c1db-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="2c1db-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="2c1db-116">Required element.</span></span><br /><br /> <span data-ttu-id="2c1db-117">Proporciona una definición de la vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="2c1db-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c1db-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2c1db-118">Parent Elements</span></span>

|<span data-ttu-id="2c1db-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c1db-119">Element</span></span>|<span data-ttu-id="2c1db-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="2c1db-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c1db-121">Elemento de control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2c1db-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="2c1db-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="2c1db-122">Required element.</span></span><br /><br /> <span data-ttu-id="2c1db-123">Define un formato de control personalizado para la vista.</span><span class="sxs-lookup"><span data-stu-id="2c1db-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c1db-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2c1db-124">Remarks</span></span>

<span data-ttu-id="2c1db-125">En la mayoría de los casos, un control tiene solo una definición, que se define en una sola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="2c1db-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="2c1db-126">Sin embargo es posible tener varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="2c1db-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="2c1db-127">En esos casos, puede definir un `CustomEntry` (elemento) para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="2c1db-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c1db-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="2c1db-128">See Also</span></span>

[<span data-ttu-id="2c1db-129">Elemento de control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2c1db-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="2c1db-130">Elemento CustomEntry para CustomEntries para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="2c1db-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2c1db-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c1db-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
