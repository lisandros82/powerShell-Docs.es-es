---
title: Elemento SelectionSetName para SelectionCondition para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855121"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="143bd-102">Elemento SelectionSetName para SelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="143bd-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="143bd-103">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="143bd-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="143bd-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra el uso de este control.</span><span class="sxs-lookup"><span data-stu-id="143bd-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="143bd-105">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="143bd-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="143bd-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionCondition para EntrySelectedBy para los controles de vista) Elemento de formato) SelectionSetName para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="143bd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="143bd-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="143bd-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="143bd-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="143bd-108">Attributes and Elements</span></span>

<span data-ttu-id="143bd-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="143bd-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="143bd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="143bd-110">Attributes</span></span>

<span data-ttu-id="143bd-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="143bd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="143bd-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="143bd-112">Child Elements</span></span>

<span data-ttu-id="143bd-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="143bd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="143bd-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="143bd-114">Parent Elements</span></span>

|<span data-ttu-id="143bd-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="143bd-115">Element</span></span>|<span data-ttu-id="143bd-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="143bd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="143bd-117">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="143bd-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="143bd-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="143bd-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="143bd-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="143bd-119">Text Value</span></span>

<span data-ttu-id="143bd-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="143bd-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="143bd-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="143bd-121">Remarks</span></span>

<span data-ttu-id="143bd-122">Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="143bd-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="143bd-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="143bd-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="143bd-124">La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="143bd-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="143bd-125">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="143bd-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="143bd-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="143bd-126">See Also</span></span>

[<span data-ttu-id="143bd-127">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="143bd-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="143bd-128">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="143bd-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="143bd-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="143bd-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="143bd-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="143bd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
