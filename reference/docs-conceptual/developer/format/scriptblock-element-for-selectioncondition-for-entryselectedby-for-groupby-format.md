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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368604"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="976b6-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="976b6-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="976b6-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="976b6-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="976b6-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="976b6-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="976b6-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="976b6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="976b6-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionCondition para EntrySelectedBy para GroupBy (Format) elemento ScriptBlock para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="976b6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="976b6-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="976b6-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="976b6-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="976b6-108">Attributes and Elements</span></span>

<span data-ttu-id="976b6-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="976b6-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="976b6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="976b6-110">Attributes</span></span>

<span data-ttu-id="976b6-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="976b6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="976b6-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="976b6-112">Child Elements</span></span>

<span data-ttu-id="976b6-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="976b6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="976b6-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="976b6-114">Parent Elements</span></span>

|<span data-ttu-id="976b6-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="976b6-115">Element</span></span>|<span data-ttu-id="976b6-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="976b6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="976b6-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="976b6-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="976b6-118">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="976b6-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="976b6-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="976b6-119">Text Value</span></span>

<span data-ttu-id="976b6-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="976b6-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="976b6-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="976b6-121">Remarks</span></span>

<span data-ttu-id="976b6-122">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="976b6-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="976b6-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="976b6-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="976b6-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="976b6-124">See Also</span></span>

[<span data-ttu-id="976b6-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="976b6-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="976b6-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="976b6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
