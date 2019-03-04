---
title: Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858021"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="f13ef-102">Elemento SelectionCondition para EntrySelectedBy for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="f13ef-103">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="f13ef-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="f13ef-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="f13ef-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f13ef-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionCondition para EntrySelectedBy para los controles de vista) Formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f13ef-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f13ef-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f13ef-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f13ef-107">Attributes and Elements</span></span>

<span data-ttu-id="f13ef-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="f13ef-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f13ef-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f13ef-109">Attributes</span></span>

<span data-ttu-id="f13ef-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f13ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f13ef-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f13ef-111">Child Elements</span></span>

|<span data-ttu-id="f13ef-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f13ef-112">Element</span></span>|<span data-ttu-id="f13ef-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="f13ef-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f13ef-114">Elemento PropertyName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f13ef-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f13ef-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f13ef-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f13ef-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f13ef-117">Elemento de bloque de script para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f13ef-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f13ef-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f13ef-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f13ef-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f13ef-120">Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f13ef-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f13ef-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f13ef-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f13ef-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f13ef-123">Elemento TypeName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f13ef-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f13ef-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f13ef-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f13ef-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f13ef-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f13ef-126">Parent Elements</span></span>

|<span data-ttu-id="f13ef-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="f13ef-127">Element</span></span>|<span data-ttu-id="f13ef-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="f13ef-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f13ef-129">Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f13ef-130">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="f13ef-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f13ef-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f13ef-131">Remarks</span></span>

<span data-ttu-id="f13ef-132">Al definir una condición de selección, se aplican los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="f13ef-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f13ef-133">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f13ef-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f13ef-134">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f13ef-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f13ef-135">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f13ef-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f13ef-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="f13ef-136">See Also</span></span>

[<span data-ttu-id="f13ef-137">Elemento PropertyName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f13ef-138">Elemento de bloque de script para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f13ef-139">Elemento SelectionSetName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f13ef-140">Elemento TypeName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f13ef-141">Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f13ef-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f13ef-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f13ef-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
