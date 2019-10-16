---
title: Elemento SelectionSetName para SelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361864"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="7667c-102">Elemento SelectionSetName para SelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7667c-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="7667c-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="7667c-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="7667c-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante este control.</span><span class="sxs-lookup"><span data-stu-id="7667c-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="7667c-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="7667c-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7667c-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para el elemento SelectionCondition GroupBy (Format) para EntrySelectedBy para GroupBy (Format) SelectionSetName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7667c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7667c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7667c-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7667c-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7667c-108">Attributes and Elements</span></span>

<span data-ttu-id="7667c-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="7667c-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7667c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7667c-110">Attributes</span></span>

<span data-ttu-id="7667c-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7667c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7667c-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7667c-112">Child Elements</span></span>

<span data-ttu-id="7667c-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7667c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7667c-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7667c-114">Parent Elements</span></span>

|<span data-ttu-id="7667c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7667c-115">Element</span></span>|<span data-ttu-id="7667c-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="7667c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7667c-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7667c-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="7667c-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="7667c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7667c-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7667c-119">Text Value</span></span>

<span data-ttu-id="7667c-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="7667c-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7667c-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7667c-121">Remarks</span></span>

<span data-ttu-id="7667c-122">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="7667c-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="7667c-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7667c-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="7667c-124">Cuando se especifica este elemento, no se puede especificar el elemento [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7667c-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="7667c-125">Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7667c-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7667c-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="7667c-126">See Also</span></span>

[<span data-ttu-id="7667c-127">Elemento TypeName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7667c-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="7667c-128">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7667c-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="7667c-129">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="7667c-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7667c-130">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="7667c-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7667c-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7667c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
