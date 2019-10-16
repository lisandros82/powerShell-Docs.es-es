---
title: Elemento ScriptBlock para SelectionCondition para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364804"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b5395-102">Elemento ScriptBlock para SelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="b5395-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b5395-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b5395-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="b5395-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="b5395-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="b5395-105">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="b5395-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5395-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionCondition View (Format) para EntrySelectedBy para los controles de la vista ( Format) elemento ScriptBlock para SelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b5395-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5395-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b5395-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5395-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b5395-108">Attributes and Elements</span></span>

<span data-ttu-id="b5395-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="b5395-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5395-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5395-110">Attributes</span></span>

<span data-ttu-id="b5395-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b5395-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5395-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b5395-112">Child Elements</span></span>

<span data-ttu-id="b5395-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b5395-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5395-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b5395-114">Parent Elements</span></span>

|<span data-ttu-id="b5395-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5395-115">Element</span></span>|<span data-ttu-id="b5395-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="b5395-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5395-117">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b5395-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b5395-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="b5395-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5395-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b5395-119">Text Value</span></span>

<span data-ttu-id="b5395-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="b5395-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5395-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b5395-121">Remarks</span></span>

<span data-ttu-id="b5395-122">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b5395-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b5395-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b5395-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5395-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="b5395-124">See Also</span></span>

[<span data-ttu-id="b5395-125">Elemento SelectionCondition para EntrySelectedBy para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b5395-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="b5395-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5395-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
