---
title: Elemento SelectionSetName para SelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368274"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="f170b-102">Elemento SelectionSetName para SelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="f170b-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="f170b-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="f170b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f170b-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra utilizando este control.</span><span class="sxs-lookup"><span data-stu-id="f170b-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="f170b-105">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="f170b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f170b-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f170b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f170b-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f170b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f170b-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f170b-108">Attributes and Elements</span></span>

<span data-ttu-id="f170b-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="f170b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f170b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f170b-110">Attributes</span></span>

<span data-ttu-id="f170b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f170b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f170b-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f170b-112">Child Elements</span></span>

<span data-ttu-id="f170b-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f170b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f170b-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f170b-114">Parent Elements</span></span>

|<span data-ttu-id="f170b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f170b-115">Element</span></span>|<span data-ttu-id="f170b-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="f170b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f170b-117">Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f170b-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="f170b-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="f170b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f170b-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f170b-119">Text Value</span></span>

<span data-ttu-id="f170b-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="f170b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f170b-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f170b-121">Remarks</span></span>

<span data-ttu-id="f170b-122">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f170b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f170b-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f170b-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="f170b-124">La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f170b-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="f170b-125">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f170b-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f170b-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="f170b-126">See Also</span></span>

[<span data-ttu-id="f170b-127">Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f170b-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="f170b-128">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="f170b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f170b-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="f170b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f170b-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f170b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
