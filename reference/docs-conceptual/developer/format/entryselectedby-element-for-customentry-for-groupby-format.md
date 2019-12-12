---
title: Elemento EntrySelectedBy para CustomEntry para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363864"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="4ad04-102">Elemento EntrySelectedBy para CustomEntry for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4ad04-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="4ad04-103">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="4ad04-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="4ad04-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="4ad04-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4ad04-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ad04-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4ad04-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ad04-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4ad04-107">Attributes and Elements</span></span>

<span data-ttu-id="4ad04-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="4ad04-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="4ad04-109">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición.</span><span class="sxs-lookup"><span data-stu-id="4ad04-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="4ad04-110">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="4ad04-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ad04-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4ad04-111">Attributes</span></span>

<span data-ttu-id="4ad04-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4ad04-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ad04-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4ad04-113">Child Elements</span></span>

|<span data-ttu-id="4ad04-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="4ad04-114">Element</span></span>|<span data-ttu-id="4ad04-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="4ad04-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ad04-116">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="4ad04-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4ad04-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4ad04-118">Define la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="4ad04-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="4ad04-119">Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="4ad04-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4ad04-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4ad04-121">Especifica un conjunto de tipos de .NET que usan esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="4ad04-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="4ad04-122">Elemento TypeName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="4ad04-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4ad04-123">Optional element.</span></span><br /><br /> <span data-ttu-id="4ad04-124">Especifica un tipo .NET que usa esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="4ad04-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4ad04-125">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4ad04-125">Parent Elements</span></span>

|<span data-ttu-id="4ad04-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="4ad04-126">Element</span></span>|<span data-ttu-id="4ad04-127">Descripción</span><span class="sxs-lookup"><span data-stu-id="4ad04-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ad04-128">Elemento CustomEntry para CustomControl para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="4ad04-129">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="4ad04-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ad04-130">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4ad04-130">Remarks</span></span>

<span data-ttu-id="4ad04-131">Las condiciones de selección se usan para definir una condición que debe existir para la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un script o un valor de propiedad específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="4ad04-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="4ad04-132">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4ad04-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ad04-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="4ad04-133">See Also</span></span>

[<span data-ttu-id="4ad04-134">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="4ad04-135">Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="4ad04-136">Elemento TypeName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="4ad04-137">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="4ad04-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="4ad04-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ad04-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
