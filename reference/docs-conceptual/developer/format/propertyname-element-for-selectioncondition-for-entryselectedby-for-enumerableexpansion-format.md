---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362324"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e0680-102">Elemento PropertyName para SelectionCondition for EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="e0680-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e0680-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e0680-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e0680-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="e0680-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="e0680-105">Elemento de configuración (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy para EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for Elemento PropertyName EnumerableExpansion (Format) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e0680-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0680-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e0680-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0680-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e0680-107">Attributes and Elements</span></span>

<span data-ttu-id="e0680-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="e0680-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0680-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0680-109">Attributes</span></span>

<span data-ttu-id="e0680-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e0680-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0680-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e0680-111">Child Elements</span></span>

<span data-ttu-id="e0680-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e0680-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0680-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e0680-113">Parent Elements</span></span>

|<span data-ttu-id="e0680-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0680-114">Element</span></span>|<span data-ttu-id="e0680-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="e0680-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0680-116">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e0680-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e0680-117">Define la condición que debe existir para expandir los objetos de colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="e0680-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e0680-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e0680-118">Text Value</span></span>

<span data-ttu-id="e0680-119">Especifique el nombre de la propiedad .NET.</span><span class="sxs-lookup"><span data-stu-id="e0680-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0680-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e0680-120">Remarks</span></span>

<span data-ttu-id="e0680-121">La condición de selección debe especificar al menos un nombre de propiedad o un script para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="e0680-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e0680-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e0680-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0680-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="e0680-123">See Also</span></span>

[<span data-ttu-id="e0680-124">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="e0680-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e0680-125">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e0680-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e0680-126">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e0680-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e0680-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0680-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
