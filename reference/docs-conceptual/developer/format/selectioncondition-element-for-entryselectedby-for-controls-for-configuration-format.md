---
title: Elemento SelectionCondition para EntrySelectedBy para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368454"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="869c5-102">Elemento SelectionCondition para EntrySelectedBy for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="869c5-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="869c5-103">Define una condición que debe existir para que se utilice una definición de control común.</span><span class="sxs-lookup"><span data-stu-id="869c5-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="869c5-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="869c5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="869c5-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para controles para Configuration (Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para CustomEntry para Configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="869c5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="869c5-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="869c5-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="869c5-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="869c5-107">Attributes and Elements</span></span>

<span data-ttu-id="869c5-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="869c5-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="869c5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="869c5-109">Attributes</span></span>

<span data-ttu-id="869c5-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="869c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="869c5-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="869c5-111">Child Elements</span></span>

|<span data-ttu-id="869c5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="869c5-112">Element</span></span>|<span data-ttu-id="869c5-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="869c5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="869c5-114">Elemento PropertyName para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="869c5-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="869c5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="869c5-116">Especifica una propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="869c5-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="869c5-117">Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="869c5-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="869c5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="869c5-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="869c5-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="869c5-120">Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="869c5-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="869c5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="869c5-122">Especifica el conjunto de tipos de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="869c5-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="869c5-123">Elemento TypeName para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="869c5-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="869c5-124">Optional element.</span></span><br /><br /> <span data-ttu-id="869c5-125">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="869c5-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="869c5-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="869c5-126">Parent Elements</span></span>

|<span data-ttu-id="869c5-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="869c5-127">Element</span></span>|<span data-ttu-id="869c5-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="869c5-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="869c5-129">Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="869c5-130">Define los tipos .NET que usan esta entrada de la definición de control común.</span><span class="sxs-lookup"><span data-stu-id="869c5-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="869c5-131">Observaciones</span><span class="sxs-lookup"><span data-stu-id="869c5-131">Remarks</span></span>

<span data-ttu-id="869c5-132">Se deben seguir las siguientes directrices al definir una condición de selección:</span><span class="sxs-lookup"><span data-stu-id="869c5-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="869c5-133">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="869c5-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="869c5-134">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="869c5-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="869c5-135">Para obtener más información sobre cómo se pueden usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="869c5-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="869c5-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="869c5-136">See Also</span></span>

[<span data-ttu-id="869c5-137">Elemento PropertyName para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="869c5-138">Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="869c5-139">Elemento SelectionSetName de SelectionCondition para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="869c5-140">Elemento TypeName para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="869c5-141">Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="869c5-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="869c5-142">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="869c5-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
