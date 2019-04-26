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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066607"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="9e8b6-102">Elemento CustomEntries para CustomControl for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="9e8b6-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9e8b6-103">Proporciona las definiciones de un control común.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="9e8b6-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9e8b6-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Formato)</span><span class="sxs-lookup"><span data-stu-id="9e8b6-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e8b6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e8b6-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e8b6-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9e8b6-107">Attributes and Elements</span></span>

<span data-ttu-id="9e8b6-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="9e8b6-109">Debe especificar uno o más elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e8b6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9e8b6-110">Attributes</span></span>

<span data-ttu-id="9e8b6-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e8b6-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9e8b6-112">Child Elements</span></span>

|<span data-ttu-id="9e8b6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e8b6-113">Element</span></span>|<span data-ttu-id="9e8b6-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="9e8b6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e8b6-115">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9e8b6-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="9e8b6-116">Proporciona una definición del control común.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9e8b6-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9e8b6-117">Parent Elements</span></span>

|<span data-ttu-id="9e8b6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e8b6-118">Element</span></span>|<span data-ttu-id="9e8b6-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="9e8b6-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e8b6-120">Elemento de control personalizado para el Control de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9e8b6-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="9e8b6-121">Define un control común.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e8b6-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9e8b6-122">Remarks</span></span>

<span data-ttu-id="9e8b6-123">En la mayoría de los casos, un control tiene solo una definición, que se define en una sola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="9e8b6-124">Sin embargo es posible tener varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="9e8b6-125">En esos casos, puede definir un `CustomEntry` (elemento) para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="9e8b6-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e8b6-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="9e8b6-126">See Also</span></span>

[<span data-ttu-id="9e8b6-127">Elemento de control personalizado para el Control de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9e8b6-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9e8b6-128">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9e8b6-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="9e8b6-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e8b6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
