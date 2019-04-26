---
title: Elemento EntrySelectedBy para CustomEntry para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066284"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="ffd2b-102">Elemento EntrySelectedBy para CustomEntry for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="ffd2b-103">Define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="ffd2b-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ffd2b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ffd2b-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ffd2b-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ffd2b-106">Attributes and Elements</span></span>

<span data-ttu-id="ffd2b-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ffd2b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ffd2b-108">Attributes</span></span>

<span data-ttu-id="ffd2b-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ffd2b-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ffd2b-110">Child Elements</span></span>

|<span data-ttu-id="ffd2b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="ffd2b-111">Element</span></span>|<span data-ttu-id="ffd2b-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="ffd2b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ffd2b-113">Elemento SelectionCondition para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="ffd2b-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ffd2b-115">Define la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ffd2b-116">Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="ffd2b-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ffd2b-118">Especifica un conjunto de tipos de .NET que usan esta definición de la vista de control.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="ffd2b-119">Elemento TypeName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="ffd2b-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ffd2b-121">Especifica un tipo .NET que usa esta definición de la vista de control.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ffd2b-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ffd2b-122">Parent Elements</span></span>

|<span data-ttu-id="ffd2b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ffd2b-123">Element</span></span>|<span data-ttu-id="ffd2b-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="ffd2b-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ffd2b-125">Elemento CustomEntry para CustomEntries para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="ffd2b-126">Define los controles utilizados por objetos específicos. NET.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ffd2b-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ffd2b-127">Remarks</span></span>

<span data-ttu-id="ffd2b-128">Debe especificar al menos un tipo, el conjunto de selección o condición de selección de una entrada.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="ffd2b-129">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="ffd2b-130">Condiciones de selección se usan para definir una condición que debe existir para la entrada que se usará, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un valor de propiedad específicos o secuencias de comandos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="ffd2b-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="ffd2b-131">Para obtener más información acerca de las condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ffd2b-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ffd2b-132">Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [vista personalizada de Control](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ffd2b-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ffd2b-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="ffd2b-133">See Also</span></span>

[<span data-ttu-id="ffd2b-134">Elemento SelectionCondition para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="ffd2b-135">Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ffd2b-136">Elemento TypeName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ffd2b-137">Elemento CustomEntry para CustomEntries para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ffd2b-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ffd2b-138">Vista de Control personalizado</span><span class="sxs-lookup"><span data-stu-id="ffd2b-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ffd2b-139">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffd2b-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
