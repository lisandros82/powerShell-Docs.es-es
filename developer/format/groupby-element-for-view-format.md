---
title: Elemento GroupBy para vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859531"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="8c964-102">Elemento GroupBy para View (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="8c964-103">Define cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="8c964-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="8c964-104">Este elemento se usa al definir una tabla, lista, vista de control personalizado o anchos.</span><span class="sxs-lookup"><span data-stu-id="8c964-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="8c964-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c964-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8c964-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c964-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8c964-107">Attributes and Elements</span></span>

<span data-ttu-id="8c964-108">Las siguientes secciones describen los atributos, elementos secundarios y elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="8c964-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c964-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c964-109">Attributes</span></span>

<span data-ttu-id="8c964-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8c964-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c964-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8c964-111">Child Elements</span></span>

|<span data-ttu-id="8c964-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c964-112">Element</span></span>|<span data-ttu-id="8c964-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="8c964-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c964-114">Elemento de control personalizado para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="8c964-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8c964-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8c964-116">Define el control personalizado que se muestran los nuevos grupos.</span><span class="sxs-lookup"><span data-stu-id="8c964-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="8c964-117">Elemento CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="8c964-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8c964-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8c964-119">Especifica el nombre de un control que se usa para mostrar el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="8c964-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="8c964-120">Elemento de etiqueta para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="8c964-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8c964-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8c964-122">Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="8c964-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="8c964-123">Elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="8c964-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8c964-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8c964-125">Especifica la propiedad de .NET en el se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="8c964-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="8c964-126">Elemento de bloque de script para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="8c964-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8c964-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8c964-128">Especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="8c964-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8c964-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8c964-129">Parent Elements</span></span>

|<span data-ttu-id="8c964-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c964-130">Element</span></span>|<span data-ttu-id="8c964-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="8c964-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c964-132">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="8c964-133">Define una vista que muestra uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="8c964-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8c964-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8c964-134">Remarks</span></span>

<span data-ttu-id="8c964-135">Al definir cómo se muestra un nuevo grupo de objetos, debe especificar la propiedad o el script que se iniciará el nuevo grupo; Sin embargo, no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="8c964-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c964-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="8c964-136">See Also</span></span>

[<span data-ttu-id="8c964-137">Elemento CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="8c964-138">Elemento de etiqueta para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="8c964-139">Elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="8c964-140">Elemento de bloque de script para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="8c964-141">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8c964-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="8c964-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c964-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
