---
title: Elemento CustomEntries para el control personalizado para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853681"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="c7ce9-102">Elemento CustomEntries para CustomControl for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c7ce9-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="c7ce9-103">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-103">Provides the definitions for the control.</span></span> <span data-ttu-id="c7ce9-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c7ce9-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento para el elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c7ce9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7ce9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c7ce9-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7ce9-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="c7ce9-107">Attributes and Elements</span></span>

<span data-ttu-id="c7ce9-108">Las secciones siguientes describen los atributos, elementos secundarios y elementos primarios de la `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="c7ce9-109">No hay ningún límite máximo para el número de elementos secundarios que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7ce9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c7ce9-110">Attributes</span></span>

<span data-ttu-id="c7ce9-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7ce9-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="c7ce9-112">Child Elements</span></span>

|<span data-ttu-id="c7ce9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7ce9-113">Element</span></span>|<span data-ttu-id="c7ce9-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="c7ce9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7ce9-115">Elemento CustomEntry para el control personalizado para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c7ce9-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="c7ce9-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-116">Required element.</span></span><br /><br /> <span data-ttu-id="c7ce9-117">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7ce9-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="c7ce9-118">Parent Elements</span></span>

|<span data-ttu-id="c7ce9-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7ce9-119">Element</span></span>|<span data-ttu-id="c7ce9-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="c7ce9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7ce9-121">Elemento de control personalizado para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c7ce9-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="c7ce9-122">Define el control personalizado que muestra el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c7ce9-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c7ce9-123">Remarks</span></span>

<span data-ttu-id="c7ce9-124">En la mayoría de los casos, un control tiene solo una definición, que se especifica en una sola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="c7ce9-125">Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar los diferentes grupos.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="c7ce9-126">En esos casos, puede definir un `CustomEntry` (elemento) para un grupo.</span><span class="sxs-lookup"><span data-stu-id="c7ce9-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ce9-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="c7ce9-127">See Also</span></span>

[<span data-ttu-id="c7ce9-128">Elemento CustomEntry para CustomEntries para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c7ce9-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="c7ce9-129">Elemento de control personalizado para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c7ce9-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="c7ce9-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7ce9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
