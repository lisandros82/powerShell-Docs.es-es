---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361924"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="19dff-102">Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="19dff-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="19dff-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="19dff-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="19dff-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra con esta definición de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="19dff-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="19dff-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format) SelectionSetName para SelectionCondition for EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="19dff-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19dff-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="19dff-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19dff-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="19dff-107">Attributes and Elements</span></span>

<span data-ttu-id="19dff-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="19dff-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19dff-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="19dff-109">Attributes</span></span>

<span data-ttu-id="19dff-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="19dff-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19dff-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="19dff-111">Child Elements</span></span>

<span data-ttu-id="19dff-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="19dff-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19dff-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="19dff-113">Parent Elements</span></span>

|<span data-ttu-id="19dff-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="19dff-114">Element</span></span>|<span data-ttu-id="19dff-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="19dff-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19dff-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19dff-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="19dff-117">Define la condición que debe existir para usar para esta definición de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="19dff-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19dff-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="19dff-118">Text Value</span></span>

<span data-ttu-id="19dff-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="19dff-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="19dff-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="19dff-120">Remarks</span></span>

<span data-ttu-id="19dff-121">La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="19dff-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="19dff-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="19dff-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="19dff-123">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="19dff-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="19dff-124">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="19dff-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="19dff-125">Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="19dff-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19dff-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="19dff-126">See Also</span></span>

[<span data-ttu-id="19dff-127">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="19dff-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="19dff-128">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="19dff-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="19dff-129">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19dff-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="19dff-130">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19dff-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="19dff-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="19dff-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
