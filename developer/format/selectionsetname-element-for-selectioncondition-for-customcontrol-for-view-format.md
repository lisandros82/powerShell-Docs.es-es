---
title: Elemento SelectionSetName para SelectionCondition para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862771"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e1700-102">Elemento SelectionSetName para SelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="e1700-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e1700-103">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="e1700-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e1700-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra el uso de este control.</span><span class="sxs-lookup"><span data-stu-id="e1700-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="e1700-105">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="e1700-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e1700-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e1700-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1700-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e1700-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1700-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e1700-108">Attributes and Elements</span></span>

<span data-ttu-id="e1700-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e1700-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1700-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1700-110">Attributes</span></span>

<span data-ttu-id="e1700-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1700-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1700-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e1700-112">Child Elements</span></span>

<span data-ttu-id="e1700-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1700-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1700-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e1700-114">Parent Elements</span></span>

|<span data-ttu-id="e1700-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1700-115">Element</span></span>|<span data-ttu-id="e1700-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="e1700-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1700-117">Elemento SelectionCondition para EntrySelectedBy para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e1700-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="e1700-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="e1700-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1700-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e1700-119">Text Value</span></span>

<span data-ttu-id="e1700-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="e1700-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1700-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e1700-121">Remarks</span></span>

<span data-ttu-id="e1700-122">Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="e1700-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e1700-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e1700-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e1700-124">La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="e1700-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e1700-125">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e1700-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1700-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="e1700-126">See Also</span></span>

[<span data-ttu-id="e1700-127">Elemento SelectionCondition para EntrySelectedBy para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e1700-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="e1700-128">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="e1700-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e1700-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="e1700-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e1700-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1700-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
