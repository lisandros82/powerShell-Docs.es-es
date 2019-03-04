---
title: Elemento CustomEntries para el control personalizado para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856311"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="8f818-102">Elemento CustomEntries para CustomControl for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="8f818-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8f818-103">Proporciona las definiciones de un control común.</span><span class="sxs-lookup"><span data-stu-id="8f818-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="8f818-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="8f818-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8f818-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Formato)</span><span class="sxs-lookup"><span data-stu-id="8f818-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f818-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8f818-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f818-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8f818-107">Attributes and Elements</span></span>

<span data-ttu-id="8f818-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f818-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="8f818-109">Debe especificar uno o más elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="8f818-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f818-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f818-110">Attributes</span></span>

<span data-ttu-id="8f818-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8f818-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f818-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8f818-112">Child Elements</span></span>

|<span data-ttu-id="8f818-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f818-113">Element</span></span>|<span data-ttu-id="8f818-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="8f818-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f818-115">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="8f818-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="8f818-116">Proporciona una definición del control común.</span><span class="sxs-lookup"><span data-stu-id="8f818-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f818-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8f818-117">Parent Elements</span></span>

|<span data-ttu-id="8f818-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f818-118">Element</span></span>|<span data-ttu-id="8f818-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="8f818-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f818-120">Elemento de control personalizado para el Control de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="8f818-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="8f818-121">Define un control común.</span><span class="sxs-lookup"><span data-stu-id="8f818-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f818-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8f818-122">Remarks</span></span>

<span data-ttu-id="8f818-123">En la mayoría de los casos, un control tiene solo una definición, que se define en una sola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f818-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="8f818-124">Sin embargo es posible tener varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="8f818-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="8f818-125">En esos casos, puede definir un `CustomEntry` (elemento) para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="8f818-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f818-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="8f818-126">See Also</span></span>

[<span data-ttu-id="8f818-127">Elemento de control personalizado para el Control de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="8f818-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8f818-128">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="8f818-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="8f818-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f818-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
