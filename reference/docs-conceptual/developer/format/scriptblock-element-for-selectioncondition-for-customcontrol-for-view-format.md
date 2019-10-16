---
title: Elemento ScriptBlock para SelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368644"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="f6155-102">Elemento ScriptBlock para SelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="f6155-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="f6155-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f6155-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f6155-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="f6155-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="f6155-105">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="f6155-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f6155-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para la vista (Format) elemento SelectionCondition para EntrySelectedBy para CustomControl para el elemento ScriptBlock de View (Format) para SelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f6155-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6155-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f6155-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6155-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f6155-108">Attributes and Elements</span></span>

<span data-ttu-id="f6155-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="f6155-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6155-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f6155-110">Attributes</span></span>

<span data-ttu-id="f6155-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f6155-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6155-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f6155-112">Child Elements</span></span>

<span data-ttu-id="f6155-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f6155-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f6155-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f6155-114">Parent Elements</span></span>

|<span data-ttu-id="f6155-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6155-115">Element</span></span>|<span data-ttu-id="f6155-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="f6155-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6155-117">Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f6155-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="f6155-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="f6155-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f6155-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f6155-119">Text Value</span></span>

<span data-ttu-id="f6155-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="f6155-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6155-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f6155-121">Remarks</span></span>

<span data-ttu-id="f6155-122">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f6155-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f6155-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f6155-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6155-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="f6155-124">See Also</span></span>

[<span data-ttu-id="f6155-125">Elemento SelectionCondition para EntrySelectedBy para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="f6155-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="f6155-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6155-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
