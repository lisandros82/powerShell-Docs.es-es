---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368404"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="44bd7-102">Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="44bd7-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="44bd7-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="44bd7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="44bd7-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra con esta definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="44bd7-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="44bd7-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44bd7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44bd7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="44bd7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44bd7-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="44bd7-107">Attributes and Elements</span></span>

<span data-ttu-id="44bd7-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="44bd7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44bd7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="44bd7-109">Attributes</span></span>

<span data-ttu-id="44bd7-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="44bd7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44bd7-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="44bd7-111">Child Elements</span></span>

<span data-ttu-id="44bd7-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="44bd7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="44bd7-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="44bd7-113">Parent Elements</span></span>

|<span data-ttu-id="44bd7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="44bd7-114">Element</span></span>|<span data-ttu-id="44bd7-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="44bd7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44bd7-116">Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44bd7-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="44bd7-117">Define la condición que debe existir para usar esta definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="44bd7-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="44bd7-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="44bd7-118">Text Value</span></span>

<span data-ttu-id="44bd7-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="44bd7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="44bd7-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="44bd7-120">Remarks</span></span>

<span data-ttu-id="44bd7-121">La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="44bd7-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="44bd7-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="44bd7-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="44bd7-123">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="44bd7-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="44bd7-124">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="44bd7-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="44bd7-125">Para obtener más información sobre otros componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="44bd7-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44bd7-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="44bd7-126">See Also</span></span>

[<span data-ttu-id="44bd7-127">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="44bd7-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="44bd7-128">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="44bd7-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="44bd7-129">Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="44bd7-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="44bd7-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="44bd7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
