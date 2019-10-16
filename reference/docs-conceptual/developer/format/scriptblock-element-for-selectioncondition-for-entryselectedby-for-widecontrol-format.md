---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368564"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="89bf9-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="89bf9-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="89bf9-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="89bf9-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="89bf9-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición de entrada ancha.</span><span class="sxs-lookup"><span data-stu-id="89bf9-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="89bf9-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy para WideEntry (Format) elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="89bf9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89bf9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="89bf9-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89bf9-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="89bf9-107">Attributes and Elements</span></span>

<span data-ttu-id="89bf9-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="89bf9-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89bf9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="89bf9-109">Attributes</span></span>

<span data-ttu-id="89bf9-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="89bf9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89bf9-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="89bf9-111">Child Elements</span></span>

<span data-ttu-id="89bf9-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="89bf9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="89bf9-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="89bf9-113">Parent Elements</span></span>

|<span data-ttu-id="89bf9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="89bf9-114">Element</span></span>|<span data-ttu-id="89bf9-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="89bf9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89bf9-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="89bf9-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="89bf9-117">Define la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="89bf9-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="89bf9-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="89bf9-118">Text Value</span></span>

<span data-ttu-id="89bf9-119">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="89bf9-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="89bf9-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="89bf9-120">Remarks</span></span>

<span data-ttu-id="89bf9-121">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="89bf9-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="89bf9-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="89bf9-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="89bf9-123">Para obtener más información sobre otros componentes de una vista amplia, vea [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="89bf9-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89bf9-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="89bf9-124">See Also</span></span>

[<span data-ttu-id="89bf9-125">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="89bf9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="89bf9-126">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="89bf9-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="89bf9-127">Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="89bf9-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="89bf9-128">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="89bf9-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="89bf9-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="89bf9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
