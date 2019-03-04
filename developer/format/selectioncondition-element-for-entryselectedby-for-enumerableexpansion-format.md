---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858291"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="92cfb-102">Elemento SelectionCondition para EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="92cfb-103">Define la condición que debe existir para expandir los objetos de la colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="92cfb-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="92cfb-104">Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración (elemento) SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92cfb-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="92cfb-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92cfb-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="92cfb-106">Attributes and Elements</span></span>

<span data-ttu-id="92cfb-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="92cfb-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="92cfb-108">Debe especificar una sola `PropertyName` o `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="92cfb-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="92cfb-109">El `SelectionSetName` y `TypeName` elementos son opcionales.</span><span class="sxs-lookup"><span data-stu-id="92cfb-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="92cfb-110">Puede especificar uno de cualquier elemento.</span><span class="sxs-lookup"><span data-stu-id="92cfb-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92cfb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="92cfb-111">Attributes</span></span>

<span data-ttu-id="92cfb-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="92cfb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92cfb-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="92cfb-113">Child Elements</span></span>

|<span data-ttu-id="92cfb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="92cfb-114">Element</span></span>|<span data-ttu-id="92cfb-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="92cfb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92cfb-116">Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="92cfb-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92cfb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="92cfb-118">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="92cfb-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="92cfb-119">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="92cfb-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92cfb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="92cfb-121">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="92cfb-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="92cfb-122">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="92cfb-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92cfb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="92cfb-124">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="92cfb-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="92cfb-125">Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="92cfb-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92cfb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="92cfb-127">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="92cfb-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="92cfb-128">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="92cfb-128">Parent Elements</span></span>

|<span data-ttu-id="92cfb-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="92cfb-129">Element</span></span>|<span data-ttu-id="92cfb-130">Descripción</span><span class="sxs-lookup"><span data-stu-id="92cfb-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92cfb-131">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="92cfb-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="92cfb-132">Define los objetos de colección de .NET se expanden por esta definición.</span><span class="sxs-lookup"><span data-stu-id="92cfb-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="92cfb-133">Observaciones</span><span class="sxs-lookup"><span data-stu-id="92cfb-133">Remarks</span></span>

<span data-ttu-id="92cfb-134">Cada definición debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="92cfb-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="92cfb-135">Al definir una condición de selección, se aplican los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="92cfb-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="92cfb-136">La condición de selección debe especificar un nombre menos de una propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="92cfb-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="92cfb-137">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="92cfb-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="92cfb-138">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para los datos de la visualización](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="92cfb-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="92cfb-139">Para obtener más información sobre otros componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="92cfb-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92cfb-140">Véase también</span><span class="sxs-lookup"><span data-stu-id="92cfb-140">See Also</span></span>

[<span data-ttu-id="92cfb-141">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="92cfb-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="92cfb-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="92cfb-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
