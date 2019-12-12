---
title: Elemento SelectionCondition para EntrySelectedBy para CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368444"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="60fab-102">Elemento SelectionCondition para EntrySelectedBy for CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="60fab-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="60fab-103">Define una condición que debe existir para que se use una definición de control.</span><span class="sxs-lookup"><span data-stu-id="60fab-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="60fab-104">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="60fab-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="60fab-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para el elemento EntrySelectedBy View (Format) para CustomEntry para CustomControl para el elemento SelectionCondition de View (Format) para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60fab-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="60fab-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60fab-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="60fab-107">Attributes and Elements</span></span>

<span data-ttu-id="60fab-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="60fab-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60fab-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="60fab-109">Attributes</span></span>

<span data-ttu-id="60fab-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="60fab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60fab-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="60fab-111">Child Elements</span></span>

|<span data-ttu-id="60fab-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="60fab-112">Element</span></span>|<span data-ttu-id="60fab-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="60fab-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60fab-114">Elemento PropertyName para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="60fab-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="60fab-115">Optional element.</span></span><br /><br /> <span data-ttu-id="60fab-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="60fab-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="60fab-117">Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="60fab-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="60fab-118">Optional element.</span></span><br /><br /> <span data-ttu-id="60fab-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="60fab-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="60fab-120">Elemento SelectionSetName para SelectionCondition para el control personalizado de View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="60fab-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="60fab-121">Optional element.</span></span><br /><br /> <span data-ttu-id="60fab-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="60fab-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="60fab-123">Elemento TypeName para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="60fab-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="60fab-124">Optional element.</span></span><br /><br /> <span data-ttu-id="60fab-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="60fab-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="60fab-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="60fab-126">Parent Elements</span></span>

|<span data-ttu-id="60fab-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="60fab-127">Element</span></span>|<span data-ttu-id="60fab-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="60fab-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60fab-129">Elemento EntrySelectedBy para CustomEntry para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="60fab-130">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="60fab-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="60fab-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="60fab-131">Remarks</span></span>

<span data-ttu-id="60fab-132">Cuando se define una condición de selección, se aplican los requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="60fab-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="60fab-133">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="60fab-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="60fab-134">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="60fab-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="60fab-135">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="60fab-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60fab-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="60fab-136">See Also</span></span>

[<span data-ttu-id="60fab-137">Elemento PropertyName para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="60fab-138">Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="60fab-139">Elemento SelectionSetName para SelectionCondition para el control personalizado de View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="60fab-140">Elemento TypeName para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="60fab-141">Elemento EntrySelectedBy para CustomEntry para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="60fab-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="60fab-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="60fab-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
