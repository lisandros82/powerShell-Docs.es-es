---
title: Elemento SelectionCondition para EntrySelectedBy para el control personalizado (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075756"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="085fe-102">Elemento SelectionCondition para EntrySelectedBy for CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="085fe-103">Define una condición que debe existir para usarse en una definición de control.</span><span class="sxs-lookup"><span data-stu-id="085fe-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="085fe-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="085fe-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="085fe-105">Configuración (formato) elemento ViewDefinitions (formato) Vista (formato) del elemento control personalizado elemento de vista (formato) del elemento CustomEntries para el control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para el control personalizado para la vista ( Elemento de formato) CustomItem para CustomEntry para el control personalizado de vista (formato) del elemento EntrySelectedBy para CustomEntry para el control personalizado de vista (formato) del elemento SelectionCondition para EntrySelectedBy para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="085fe-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="085fe-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="085fe-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="085fe-107">Attributes and Elements</span></span>

<span data-ttu-id="085fe-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="085fe-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="085fe-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="085fe-109">Attributes</span></span>

<span data-ttu-id="085fe-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="085fe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="085fe-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="085fe-111">Child Elements</span></span>

|<span data-ttu-id="085fe-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="085fe-112">Element</span></span>|<span data-ttu-id="085fe-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="085fe-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="085fe-114">Elemento PropertyName para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="085fe-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="085fe-115">Optional element.</span></span><br /><br /> <span data-ttu-id="085fe-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="085fe-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="085fe-117">Elemento de bloque de script para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="085fe-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="085fe-118">Optional element.</span></span><br /><br /> <span data-ttu-id="085fe-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="085fe-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="085fe-120">Elemento SelectionSetName para SelectionCondition para un Control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="085fe-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="085fe-121">Optional element.</span></span><br /><br /> <span data-ttu-id="085fe-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="085fe-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="085fe-123">Elemento TypeName para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="085fe-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="085fe-124">Optional element.</span></span><br /><br /> <span data-ttu-id="085fe-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="085fe-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="085fe-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="085fe-126">Parent Elements</span></span>

|<span data-ttu-id="085fe-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="085fe-127">Element</span></span>|<span data-ttu-id="085fe-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="085fe-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="085fe-129">Elemento EntrySelectedBy para CustomEntry para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="085fe-130">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="085fe-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="085fe-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="085fe-131">Remarks</span></span>

<span data-ttu-id="085fe-132">Al definir una condición de selección, se aplican los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="085fe-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="085fe-133">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="085fe-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="085fe-134">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="085fe-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="085fe-135">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="085fe-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="085fe-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="085fe-136">See Also</span></span>

[<span data-ttu-id="085fe-137">Elemento PropertyName para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="085fe-138">Elemento de bloque de script para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="085fe-139">Elemento SelectionSetName para SelectionCondition para un Control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="085fe-140">Elemento TypeName para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="085fe-141">Elemento EntrySelectedBy para CustomEntry para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="085fe-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="085fe-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="085fe-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
