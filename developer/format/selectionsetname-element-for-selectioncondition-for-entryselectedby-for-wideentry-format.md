---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854131"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="3e590-102">Elemento SelectionSetName para SelectionCondition for EntrySelectedBy for WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3e590-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="3e590-103">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="3e590-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="3e590-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de esta definición de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="3e590-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="3e590-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para WideEntry (formato) (elemento) SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3e590-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e590-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3e590-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e590-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3e590-107">Attributes and Elements</span></span>

<span data-ttu-id="3e590-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="3e590-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e590-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e590-109">Attributes</span></span>

<span data-ttu-id="3e590-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3e590-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e590-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3e590-111">Child Elements</span></span>

<span data-ttu-id="3e590-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3e590-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e590-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3e590-113">Parent Elements</span></span>

|<span data-ttu-id="3e590-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e590-114">Element</span></span>|<span data-ttu-id="3e590-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e590-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e590-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3e590-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="3e590-117">Define la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="3e590-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3e590-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3e590-118">Text Value</span></span>

<span data-ttu-id="3e590-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="3e590-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e590-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3e590-120">Remarks</span></span>

<span data-ttu-id="3e590-121">La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3e590-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="3e590-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3e590-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3e590-123">Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="3e590-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="3e590-124">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3e590-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="3e590-125">Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3e590-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e590-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="3e590-126">See Also</span></span>

[<span data-ttu-id="3e590-127">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="3e590-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3e590-128">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="3e590-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3e590-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="3e590-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3e590-130">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3e590-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3e590-131">Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3e590-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3e590-132">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e590-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
