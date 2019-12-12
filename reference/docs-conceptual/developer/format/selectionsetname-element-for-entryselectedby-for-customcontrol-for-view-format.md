---
title: Elemento SelectionSetName para EntrySelectedBy para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364754"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="b8826-102">Elemento SelectionSetName para EntrySelectedBy for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="b8826-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="b8826-103">Especifica un conjunto de objetos .NET para la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="b8826-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="b8826-104">No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="b8826-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="b8826-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para el elemento SelectionSetName de View (Format) para EntrySelectedBy para CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b8826-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8826-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b8826-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8826-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b8826-107">Attributes and Elements</span></span>

<span data-ttu-id="b8826-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="b8826-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8826-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8826-109">Attributes</span></span>

<span data-ttu-id="b8826-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b8826-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8826-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b8826-111">Child Elements</span></span>

<span data-ttu-id="b8826-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b8826-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8826-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b8826-113">Parent Elements</span></span>

|<span data-ttu-id="b8826-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8826-114">Element</span></span>|<span data-ttu-id="b8826-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="b8826-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8826-116">Elemento EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8826-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b8826-117">Define los tipos .NET que usan esta entrada personalizada o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="b8826-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b8826-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b8826-118">Text Value</span></span>

<span data-ttu-id="b8826-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="b8826-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8826-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b8826-120">Remarks</span></span>

<span data-ttu-id="b8826-121">Cada entrada de control personalizada debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="b8826-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b8826-122">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="b8826-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b8826-123">Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="b8826-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b8826-124">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b8826-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b8826-125">Para obtener más información sobre los componentes de una vista de control personalizada, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b8826-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8826-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="b8826-126">See Also</span></span>

[<span data-ttu-id="b8826-127">Elemento EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8826-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b8826-128">Vista de control personalizada</span><span class="sxs-lookup"><span data-stu-id="b8826-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b8826-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8826-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
