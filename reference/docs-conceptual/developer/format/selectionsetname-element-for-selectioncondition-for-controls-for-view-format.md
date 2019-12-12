---
title: Elemento SelectionSetName para SelectionCondition para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361974"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="2de78-102">Elemento SelectionSetName para SelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="2de78-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="2de78-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="2de78-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="2de78-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra utilizando este control.</span><span class="sxs-lookup"><span data-stu-id="2de78-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="2de78-105">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="2de78-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2de78-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionCondition View (Format) para EntrySelectedBy para los controles de la vista ( Format) elemento SelectionSetName para SelectionCondition para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2de78-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2de78-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2de78-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2de78-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2de78-108">Attributes and Elements</span></span>

<span data-ttu-id="2de78-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="2de78-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2de78-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2de78-110">Attributes</span></span>

<span data-ttu-id="2de78-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2de78-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2de78-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2de78-112">Child Elements</span></span>

<span data-ttu-id="2de78-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2de78-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2de78-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2de78-114">Parent Elements</span></span>

|<span data-ttu-id="2de78-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="2de78-115">Element</span></span>|<span data-ttu-id="2de78-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="2de78-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2de78-117">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2de78-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="2de78-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="2de78-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2de78-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="2de78-119">Text Value</span></span>

<span data-ttu-id="2de78-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="2de78-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2de78-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2de78-121">Remarks</span></span>

<span data-ttu-id="2de78-122">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="2de78-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="2de78-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2de78-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="2de78-124">La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2de78-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="2de78-125">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2de78-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2de78-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="2de78-126">See Also</span></span>

[<span data-ttu-id="2de78-127">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2de78-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="2de78-128">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="2de78-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2de78-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="2de78-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2de78-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2de78-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
