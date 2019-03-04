---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860421"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="b62ec-102">Elemento PropertyName para SelectionCondition for EntrySelectedBy for WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b62ec-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="b62ec-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b62ec-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b62ec-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="b62ec-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="b62ec-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para WideEntry (formato) elemento PropertyName SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b62ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b62ec-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b62ec-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b62ec-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b62ec-107">Attributes and Elements</span></span>

<span data-ttu-id="b62ec-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b62ec-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b62ec-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b62ec-109">Attributes</span></span>

<span data-ttu-id="b62ec-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b62ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b62ec-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b62ec-111">Child Elements</span></span>

<span data-ttu-id="b62ec-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b62ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b62ec-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b62ec-113">Parent Elements</span></span>

|<span data-ttu-id="b62ec-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b62ec-114">Element</span></span>|<span data-ttu-id="b62ec-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="b62ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b62ec-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b62ec-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="b62ec-117">Define la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="b62ec-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b62ec-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b62ec-118">Text Value</span></span>

<span data-ttu-id="b62ec-119">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="b62ec-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b62ec-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b62ec-120">Remarks</span></span>

<span data-ttu-id="b62ec-121">La condición de selección debe especificar al menos un nombre de propiedad o un script para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b62ec-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b62ec-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b62ec-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b62ec-123">Para obtener más información sobre otros componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b62ec-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b62ec-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="b62ec-124">See Also</span></span>

[<span data-ttu-id="b62ec-125">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="b62ec-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b62ec-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="b62ec-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b62ec-127">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b62ec-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b62ec-128">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b62ec-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b62ec-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b62ec-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
