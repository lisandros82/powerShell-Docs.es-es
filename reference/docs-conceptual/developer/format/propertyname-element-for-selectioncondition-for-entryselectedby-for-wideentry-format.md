---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362244"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="d12e6-102">Elemento PropertyName para SelectionCondition for EntrySelectedBy for WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="d12e6-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="d12e6-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="d12e6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d12e6-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="d12e6-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="d12e6-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy para WideEntry (Format) NombreDePropiedad Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d12e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d12e6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d12e6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d12e6-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d12e6-107">Attributes and Elements</span></span>

<span data-ttu-id="d12e6-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="d12e6-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d12e6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d12e6-109">Attributes</span></span>

<span data-ttu-id="d12e6-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d12e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d12e6-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d12e6-111">Child Elements</span></span>

<span data-ttu-id="d12e6-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d12e6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d12e6-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d12e6-113">Parent Elements</span></span>

|<span data-ttu-id="d12e6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="d12e6-114">Element</span></span>|<span data-ttu-id="d12e6-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="d12e6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d12e6-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d12e6-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d12e6-117">Define la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="d12e6-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d12e6-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d12e6-118">Text Value</span></span>

<span data-ttu-id="d12e6-119">Especifique el nombre de la propiedad .NET.</span><span class="sxs-lookup"><span data-stu-id="d12e6-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d12e6-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d12e6-120">Remarks</span></span>

<span data-ttu-id="d12e6-121">La condición de selección debe especificar al menos un nombre de propiedad o un script para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d12e6-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d12e6-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d12e6-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d12e6-123">Para obtener más información sobre otros componentes de una vista amplia, vea [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d12e6-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d12e6-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="d12e6-124">See Also</span></span>

[<span data-ttu-id="d12e6-125">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="d12e6-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d12e6-126">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="d12e6-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d12e6-127">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d12e6-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d12e6-128">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d12e6-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d12e6-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d12e6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
