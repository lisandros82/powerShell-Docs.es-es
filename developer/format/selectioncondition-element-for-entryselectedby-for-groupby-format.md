---
title: Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855171"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="8fbf8-102">Elemento SelectionCondition para EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="8fbf8-103">Define una condición que debe existir para usarse en una definición de control.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="8fbf8-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8fbf8-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fbf8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8fbf8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8fbf8-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8fbf8-107">Attributes and Elements</span></span>

<span data-ttu-id="8fbf8-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fbf8-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8fbf8-109">Attributes</span></span>

<span data-ttu-id="8fbf8-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fbf8-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8fbf8-111">Child Elements</span></span>

|<span data-ttu-id="8fbf8-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="8fbf8-112">Element</span></span>|<span data-ttu-id="8fbf8-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="8fbf8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fbf8-114">Elemento PropertyName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="8fbf8-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8fbf8-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8fbf8-117">Elemento de bloque de script para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="8fbf8-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8fbf8-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8fbf8-120">Elemento SelectionSetName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="8fbf8-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8fbf8-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8fbf8-123">Elemento TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="8fbf8-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8fbf8-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8fbf8-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8fbf8-126">Parent Elements</span></span>

|<span data-ttu-id="8fbf8-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="8fbf8-127">Element</span></span>|<span data-ttu-id="8fbf8-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="8fbf8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fbf8-129">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="8fbf8-130">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8fbf8-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8fbf8-131">Remarks</span></span>

<span data-ttu-id="8fbf8-132">Al definir una condición de selección, se aplican los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="8fbf8-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8fbf8-133">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8fbf8-134">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="8fbf8-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8fbf8-135">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8fbf8-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fbf8-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="8fbf8-136">See Also</span></span>

[<span data-ttu-id="8fbf8-137">Elemento PropertyName para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8fbf8-138">Elemento de bloque de script para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8fbf8-139">Elemento SelectionSetName para SelectionCondition para un Control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8fbf8-140">Elemento TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="8fbf8-141">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8fbf8-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="8fbf8-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fbf8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
