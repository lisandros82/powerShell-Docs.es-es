---
title: Elemento PropertyName para SelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364954"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="eaea1-102">Elemento PropertyName para SelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="eaea1-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="eaea1-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="eaea1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="eaea1-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="eaea1-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="eaea1-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="eaea1-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="eaea1-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento EntrySelectedBy GroupBy (Format) para CustomEntry para el elemento SelectionCondition GroupBy (Format) para EntrySelectedBy para GroupBy (Format) PropertyName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eaea1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eaea1-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="eaea1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eaea1-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="eaea1-108">Attributes and Elements</span></span>

<span data-ttu-id="eaea1-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="eaea1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eaea1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="eaea1-110">Attributes</span></span>

<span data-ttu-id="eaea1-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="eaea1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eaea1-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="eaea1-112">Child Elements</span></span>

<span data-ttu-id="eaea1-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="eaea1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eaea1-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="eaea1-114">Parent Elements</span></span>

|<span data-ttu-id="eaea1-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="eaea1-115">Element</span></span>|<span data-ttu-id="eaea1-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="eaea1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eaea1-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eaea1-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="eaea1-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="eaea1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eaea1-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="eaea1-119">Text Value</span></span>

<span data-ttu-id="eaea1-120">Especifique el nombre de la propiedad .NET.</span><span class="sxs-lookup"><span data-stu-id="eaea1-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="eaea1-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="eaea1-121">Remarks</span></span>

<span data-ttu-id="eaea1-122">La condición de selección debe especificar al menos un nombre de propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="eaea1-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="eaea1-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="eaea1-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eaea1-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="eaea1-124">See Also</span></span>

[<span data-ttu-id="eaea1-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eaea1-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="eaea1-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eaea1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
