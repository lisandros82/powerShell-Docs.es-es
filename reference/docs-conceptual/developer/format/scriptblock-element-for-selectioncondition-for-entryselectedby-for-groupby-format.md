---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368604"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="fb070-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fb070-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="fb070-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="fb070-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fb070-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="fb070-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="fb070-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="fb070-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fb070-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionCondition para EntrySelectedBy para GroupBy (Format) elemento ScriptBlock para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fb070-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb070-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fb070-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb070-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fb070-108">Attributes and Elements</span></span>

<span data-ttu-id="fb070-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="fb070-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb070-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb070-110">Attributes</span></span>

<span data-ttu-id="fb070-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fb070-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb070-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fb070-112">Child Elements</span></span>

<span data-ttu-id="fb070-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fb070-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb070-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fb070-114">Parent Elements</span></span>

|<span data-ttu-id="fb070-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb070-115">Element</span></span>|<span data-ttu-id="fb070-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb070-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb070-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fb070-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="fb070-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="fb070-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fb070-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fb070-119">Text Value</span></span>

<span data-ttu-id="fb070-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="fb070-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb070-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fb070-121">Remarks</span></span>

<span data-ttu-id="fb070-122">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="fb070-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="fb070-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fb070-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb070-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="fb070-124">See Also</span></span>

[<span data-ttu-id="fb070-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fb070-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="fb070-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb070-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
