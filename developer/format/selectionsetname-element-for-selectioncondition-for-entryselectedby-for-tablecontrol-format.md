---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064057"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="7a6c2-102">Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a6c2-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="7a6c2-103">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="7a6c2-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de esta definición de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="7a6c2-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato) (elemento) SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7a6c2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a6c2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7a6c2-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a6c2-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7a6c2-107">Attributes and Elements</span></span>

<span data-ttu-id="7a6c2-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a6c2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a6c2-109">Attributes</span></span>

<span data-ttu-id="7a6c2-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a6c2-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7a6c2-111">Child Elements</span></span>

<span data-ttu-id="7a6c2-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a6c2-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7a6c2-113">Parent Elements</span></span>

|<span data-ttu-id="7a6c2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a6c2-114">Element</span></span>|<span data-ttu-id="7a6c2-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="7a6c2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a6c2-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7a6c2-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7a6c2-117">Define la condición que debe existir para que use para esta definición de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a6c2-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7a6c2-118">Text Value</span></span>

<span data-ttu-id="7a6c2-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a6c2-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7a6c2-120">Remarks</span></span>

<span data-ttu-id="7a6c2-121">La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="7a6c2-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7a6c2-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7a6c2-123">Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="7a6c2-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="7a6c2-124">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7a6c2-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="7a6c2-125">Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7a6c2-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a6c2-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="7a6c2-126">See Also</span></span>

[<span data-ttu-id="7a6c2-127">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="7a6c2-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7a6c2-128">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="7a6c2-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7a6c2-129">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7a6c2-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7a6c2-130">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7a6c2-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7a6c2-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a6c2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
