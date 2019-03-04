---
title: Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854151"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="3074d-102">Elemento SelectionCondition para EntrySelectedBy for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3074d-103">Define una condición que debe cumplirse para que una definición común de control que se usará.</span><span class="sxs-lookup"><span data-stu-id="3074d-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="3074d-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="3074d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3074d-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para los controles para Elemento de configuración (formato) CustomEntry para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionCondition para EntrySelectedBy para CustomEntry para Configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3074d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3074d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3074d-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3074d-107">Attributes and Elements</span></span>

<span data-ttu-id="3074d-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="3074d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3074d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3074d-109">Attributes</span></span>

<span data-ttu-id="3074d-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3074d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3074d-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3074d-111">Child Elements</span></span>

|<span data-ttu-id="3074d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3074d-112">Element</span></span>|<span data-ttu-id="3074d-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="3074d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3074d-114">Elemento PropertyName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3074d-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3074d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3074d-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="3074d-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3074d-117">Elemento de bloque de script para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3074d-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3074d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3074d-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="3074d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3074d-120">Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3074d-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3074d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3074d-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="3074d-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3074d-123">Elemento TypeName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3074d-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3074d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3074d-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="3074d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3074d-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3074d-126">Parent Elements</span></span>

|<span data-ttu-id="3074d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="3074d-127">Element</span></span>|<span data-ttu-id="3074d-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="3074d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3074d-129">Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3074d-130">Define los tipos de .NET que usan esta entrada de la definición de control comunes.</span><span class="sxs-lookup"><span data-stu-id="3074d-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3074d-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3074d-131">Remarks</span></span>

<span data-ttu-id="3074d-132">Al definir una condición de selección deben seguir las directrices siguientes:</span><span class="sxs-lookup"><span data-stu-id="3074d-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="3074d-133">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3074d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3074d-134">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3074d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3074d-135">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3074d-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3074d-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="3074d-136">See Also</span></span>

[<span data-ttu-id="3074d-137">Elemento PropertyName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3074d-138">Elemento de bloque de script para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3074d-139">Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3074d-140">Elemento TypeName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3074d-141">Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="3074d-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3074d-142">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="3074d-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
