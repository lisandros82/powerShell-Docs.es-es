---
title: Elemento PropertyName para SelectionCondition para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362364"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="ff18f-102">Elemento PropertyName para SelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="ff18f-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="ff18f-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="ff18f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ff18f-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada.</span><span class="sxs-lookup"><span data-stu-id="ff18f-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="ff18f-105">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="ff18f-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ff18f-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionCondition View (Format) para EntrySelectedBy para los controles de la vista ( Format) elemento PropertyName para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff18f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff18f-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ff18f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff18f-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ff18f-108">Attributes and Elements</span></span>

<span data-ttu-id="ff18f-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="ff18f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff18f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff18f-110">Attributes</span></span>

<span data-ttu-id="ff18f-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ff18f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff18f-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ff18f-112">Child Elements</span></span>

<span data-ttu-id="ff18f-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ff18f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ff18f-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ff18f-114">Parent Elements</span></span>

|<span data-ttu-id="ff18f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff18f-115">Element</span></span>|<span data-ttu-id="ff18f-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="ff18f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff18f-117">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff18f-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ff18f-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="ff18f-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ff18f-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ff18f-119">Text Value</span></span>

<span data-ttu-id="ff18f-120">Especifique el nombre de la propiedad .NET.</span><span class="sxs-lookup"><span data-stu-id="ff18f-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff18f-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ff18f-121">Remarks</span></span>

<span data-ttu-id="ff18f-122">La condición de selección debe especificar al menos un nombre de propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ff18f-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="ff18f-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ff18f-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff18f-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="ff18f-124">See Also</span></span>

[<span data-ttu-id="ff18f-125">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="ff18f-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="ff18f-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff18f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)