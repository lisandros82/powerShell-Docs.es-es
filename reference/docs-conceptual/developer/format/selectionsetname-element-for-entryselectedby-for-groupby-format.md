---
title: Elemento SelectionSetName para EntrySelectedBy para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364744"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="3e812-102">Elemento SelectionSetName para EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="3e812-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="3e812-103">Especifica un conjunto de objetos .NET para la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="3e812-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="3e812-104">No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="3e812-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="3e812-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="3e812-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3e812-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionSetName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3e812-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e812-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3e812-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e812-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3e812-108">Attributes and Elements</span></span>

<span data-ttu-id="3e812-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="3e812-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e812-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e812-110">Attributes</span></span>

<span data-ttu-id="3e812-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3e812-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e812-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3e812-112">Child Elements</span></span>

<span data-ttu-id="3e812-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3e812-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e812-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3e812-114">Parent Elements</span></span>

|<span data-ttu-id="3e812-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e812-115">Element</span></span>|<span data-ttu-id="3e812-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e812-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e812-117">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3e812-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3e812-118">Define los tipos .NET que usan esta entrada personalizada o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="3e812-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3e812-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3e812-119">Text Value</span></span>

<span data-ttu-id="3e812-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="3e812-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e812-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3e812-121">Remarks</span></span>

<span data-ttu-id="3e812-122">Cada definición de control personalizado debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="3e812-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3e812-123">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="3e812-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="3e812-124">Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="3e812-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="3e812-125">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3e812-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="3e812-126">Para obtener más información sobre los componentes de una vista de control personalizada, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3e812-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e812-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="3e812-127">See Also</span></span>

[<span data-ttu-id="3e812-128">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3e812-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3e812-129">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="3e812-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="3e812-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e812-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
