---
title: Elemento PropertyName para SelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362354"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="3cd6b-102">Elemento PropertyName para SelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="3cd6b-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="3cd6b-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3cd6b-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="3cd6b-105">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3cd6b-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para el elemento EntrySelectedBy de View (Format) para CustomEntry para CustomControl para el elemento SelectionCondition de View (Format) para EntrySelectedBy para CustomControl para View (Format) PropertyName Elemento para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cd6b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cd6b-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3cd6b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cd6b-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3cd6b-108">Attributes and Elements</span></span>

<span data-ttu-id="3cd6b-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cd6b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3cd6b-110">Attributes</span></span>

<span data-ttu-id="3cd6b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cd6b-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3cd6b-112">Child Elements</span></span>

<span data-ttu-id="3cd6b-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3cd6b-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3cd6b-114">Parent Elements</span></span>

|<span data-ttu-id="3cd6b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="3cd6b-115">Element</span></span>|<span data-ttu-id="3cd6b-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="3cd6b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cd6b-117">Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cd6b-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="3cd6b-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3cd6b-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3cd6b-119">Text Value</span></span>

<span data-ttu-id="3cd6b-120">Especifique el nombre de la propiedad .NET.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cd6b-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3cd6b-121">Remarks</span></span>

<span data-ttu-id="3cd6b-122">La condición de selección debe especificar al menos un nombre de propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3cd6b-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="3cd6b-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3cd6b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cd6b-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="3cd6b-124">See Also</span></span>

[<span data-ttu-id="3cd6b-125">Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cd6b-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="3cd6b-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cd6b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
