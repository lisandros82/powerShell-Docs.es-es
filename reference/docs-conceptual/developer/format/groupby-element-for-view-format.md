---
title: Elemento GroupBy para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363634"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="7a1b6-102">Elemento GroupBy para View (formato)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="7a1b6-103">Define cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="7a1b6-104">Este elemento se utiliza al definir una vista de control de tabla, lista, ancho o personalizado.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="7a1b6-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a1b6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7a1b6-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a1b6-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7a1b6-107">Attributes and Elements</span></span>

<span data-ttu-id="7a1b6-108">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a1b6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a1b6-109">Attributes</span></span>

<span data-ttu-id="7a1b6-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a1b6-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7a1b6-111">Child Elements</span></span>

|<span data-ttu-id="7a1b6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a1b6-112">Element</span></span>|<span data-ttu-id="7a1b6-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="7a1b6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a1b6-114">Elemento CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="7a1b6-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7a1b6-116">Define el control personalizado que muestra los nuevos grupos.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="7a1b6-117">Elemento CustomControlName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="7a1b6-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7a1b6-119">Especifica el nombre de un control que se usa para mostrar el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="7a1b6-120">Elemento Label para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="7a1b6-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7a1b6-122">Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="7a1b6-123">Elemento PropertyName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="7a1b6-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7a1b6-125">Especifica la propiedad de .NET que inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="7a1b6-126">Elemento ScriptBlock para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="7a1b6-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-127">Optional element.</span></span><br /><br /> <span data-ttu-id="7a1b6-128">Especifica el script que inicia un nuevo grupo siempre que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7a1b6-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7a1b6-129">Parent Elements</span></span>

|<span data-ttu-id="7a1b6-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a1b6-130">Element</span></span>|<span data-ttu-id="7a1b6-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="7a1b6-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a1b6-132">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="7a1b6-133">Define una vista que muestra uno o más objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7a1b6-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7a1b6-134">Remarks</span></span>

<span data-ttu-id="7a1b6-135">Al definir cómo se muestra un nuevo grupo de objetos, debe especificar la propiedad o el script que iniciará el nuevo grupo. sin embargo, no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7a1b6-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a1b6-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="7a1b6-136">See Also</span></span>

[<span data-ttu-id="7a1b6-137">Elemento CustomControlName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="7a1b6-138">Elemento Label para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="7a1b6-139">Elemento PropertyName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="7a1b6-140">Elemento ScriptBlock para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="7a1b6-141">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="7a1b6-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="7a1b6-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a1b6-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
