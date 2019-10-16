---
title: Elemento SelectionSetName para SelectionCondition para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368284"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="1f15d-102">Elemento SelectionSetName para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="1f15d-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1f15d-103">Especifica el conjunto de tipos de .NET que desencadenan la condición.</span><span class="sxs-lookup"><span data-stu-id="1f15d-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1f15d-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante este control.</span><span class="sxs-lookup"><span data-stu-id="1f15d-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="1f15d-105">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="1f15d-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1f15d-106">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para controles para Configuration (Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para controles para Configuration (Format) elemento SelectionSetName para SelectionCondition para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="1f15d-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f15d-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1f15d-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f15d-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1f15d-108">Attributes and Elements</span></span>

<span data-ttu-id="1f15d-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="1f15d-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f15d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1f15d-110">Attributes</span></span>

<span data-ttu-id="1f15d-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1f15d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f15d-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1f15d-112">Child Elements</span></span>

<span data-ttu-id="1f15d-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1f15d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f15d-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1f15d-114">Parent Elements</span></span>

|<span data-ttu-id="1f15d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f15d-115">Element</span></span>|<span data-ttu-id="1f15d-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="1f15d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f15d-117">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="1f15d-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="1f15d-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="1f15d-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f15d-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1f15d-119">Text Value</span></span>

<span data-ttu-id="1f15d-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="1f15d-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f15d-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1f15d-121">Remarks</span></span>

<span data-ttu-id="1f15d-122">Los conjuntos de selección son grupos comunes de objetos .NET que se pueden usar en cualquier vista que defina el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="1f15d-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1f15d-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1f15d-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1f15d-124">La condición de selección puede especificar un conjunto de selección o un tipo .NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1f15d-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1f15d-125">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f15d-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f15d-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="1f15d-126">See Also</span></span>

[<span data-ttu-id="1f15d-127">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="1f15d-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="1f15d-128">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="1f15d-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1f15d-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="1f15d-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1f15d-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f15d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
