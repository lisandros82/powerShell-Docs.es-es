---
title: Elemento EntrySelectedBy para CustomEntry para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363894"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="6432a-102">Elemento EntrySelectedBy para CustomEntry for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="6432a-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="6432a-103">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="6432a-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="6432a-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="6432a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6432a-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para controles para el elemento CustomEntry de View (Format) para CustomEntries para controles para el elemento EntrySelectedBy View (Format) para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="6432a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6432a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6432a-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6432a-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="6432a-107">Attributes and Elements</span></span>

<span data-ttu-id="6432a-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="6432a-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="6432a-109">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición.</span><span class="sxs-lookup"><span data-stu-id="6432a-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="6432a-110">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="6432a-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="6432a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6432a-111">Attributes</span></span>

<span data-ttu-id="6432a-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="6432a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6432a-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="6432a-113">Child Elements</span></span>

|<span data-ttu-id="6432a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="6432a-114">Element</span></span>|<span data-ttu-id="6432a-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="6432a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6432a-116">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="6432a-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6432a-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6432a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6432a-118">Define la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="6432a-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6432a-119">Elemento SelectionSetName para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="6432a-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6432a-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6432a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6432a-121">Especifica un conjunto de tipos de .NET que usan esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="6432a-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="6432a-122">Elemento TypeName para EntrySelectedBy para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="6432a-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6432a-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6432a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="6432a-124">Especifica un tipo .NET que usa esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="6432a-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6432a-125">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="6432a-125">Parent Elements</span></span>

|<span data-ttu-id="6432a-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6432a-126">Element</span></span>|<span data-ttu-id="6432a-127">Descripción</span><span class="sxs-lookup"><span data-stu-id="6432a-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6432a-128">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="6432a-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="6432a-129">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="6432a-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6432a-130">Observaciones</span><span class="sxs-lookup"><span data-stu-id="6432a-130">Remarks</span></span>

<span data-ttu-id="6432a-131">Las condiciones de selección se usan para definir una condición que debe existir en la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad específica o cuando un script o un valor de propiedad específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="6432a-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6432a-132">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6432a-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6432a-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="6432a-133">See Also</span></span>

[<span data-ttu-id="6432a-134">Elemento CustomEntry para CustomEntries para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="6432a-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="6432a-135">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6432a-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
