---
title: Elemento EntrySelectedBy para CustomEntry para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368784"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="caa1a-102">Elemento EntrySelectedBy para CustomEntry for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="caa1a-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="caa1a-103">Define los tipos .NET que usan esta entrada personalizada o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="caa1a-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="caa1a-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="caa1a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="caa1a-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="caa1a-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="caa1a-106">Attributes and Elements</span></span>

<span data-ttu-id="caa1a-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="caa1a-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="caa1a-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="caa1a-108">Attributes</span></span>

<span data-ttu-id="caa1a-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="caa1a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="caa1a-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="caa1a-110">Child Elements</span></span>

|<span data-ttu-id="caa1a-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="caa1a-111">Element</span></span>|<span data-ttu-id="caa1a-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="caa1a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="caa1a-113">Elemento SelectionCondition para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="caa1a-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="caa1a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="caa1a-115">Define la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="caa1a-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="caa1a-116">Elemento SelectionSetName para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="caa1a-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="caa1a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="caa1a-118">Especifica un conjunto de tipos de .NET que usan esta definición de la vista de control.</span><span class="sxs-lookup"><span data-stu-id="caa1a-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="caa1a-119">Elemento TypeName para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="caa1a-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="caa1a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="caa1a-121">Especifica un tipo .NET que usa esta definición de la vista de control.</span><span class="sxs-lookup"><span data-stu-id="caa1a-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="caa1a-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="caa1a-122">Parent Elements</span></span>

|<span data-ttu-id="caa1a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="caa1a-123">Element</span></span>|<span data-ttu-id="caa1a-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="caa1a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="caa1a-125">Elemento CustomEntry para CustomEntries para View (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="caa1a-126">Define los controles utilizados por objetos .NET concretos.</span><span class="sxs-lookup"><span data-stu-id="caa1a-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="caa1a-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="caa1a-127">Remarks</span></span>

<span data-ttu-id="caa1a-128">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una entrada.</span><span class="sxs-lookup"><span data-stu-id="caa1a-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="caa1a-129">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="caa1a-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="caa1a-130">Las condiciones de selección se usan para definir una condición que debe existir para la entrada que se va a usar, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un script o un valor de propiedad específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="caa1a-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="caa1a-131">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="caa1a-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="caa1a-132">Para obtener más información sobre los componentes de una vista de control personalizada, vea [vista de control personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="caa1a-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="caa1a-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="caa1a-133">See Also</span></span>

[<span data-ttu-id="caa1a-134">Elemento SelectionCondition para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="caa1a-135">Elemento SelectionSetName para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="caa1a-136">Elemento TypeName para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="caa1a-137">Elemento CustomEntry para CustomEntries para View (Format)</span><span class="sxs-lookup"><span data-stu-id="caa1a-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="caa1a-138">Vista de control personalizada</span><span class="sxs-lookup"><span data-stu-id="caa1a-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="caa1a-139">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="caa1a-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
