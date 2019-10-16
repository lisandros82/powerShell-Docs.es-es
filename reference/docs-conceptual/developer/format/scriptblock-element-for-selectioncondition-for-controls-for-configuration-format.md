---
title: Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368624"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="bbc9d-102">Elemento ScriptBlock para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="bbc9d-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bbc9d-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bbc9d-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="bbc9d-105">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bbc9d-106">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para controles de configuración (Format) Elemento ScriptBlock para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc9d-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbc9d-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bbc9d-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbc9d-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="bbc9d-108">Attributes and Elements</span></span>

<span data-ttu-id="bbc9d-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbc9d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bbc9d-110">Attributes</span></span>

<span data-ttu-id="bbc9d-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbc9d-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="bbc9d-112">Child Elements</span></span>

<span data-ttu-id="bbc9d-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbc9d-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="bbc9d-114">Parent Elements</span></span>

|<span data-ttu-id="bbc9d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbc9d-115">Element</span></span>|<span data-ttu-id="bbc9d-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="bbc9d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbc9d-117">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc9d-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="bbc9d-118">Define una condición que debe existir para que se use la definición de control común.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bbc9d-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bbc9d-119">Text Value</span></span>

<span data-ttu-id="bbc9d-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbc9d-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bbc9d-121">Remarks</span></span>

<span data-ttu-id="bbc9d-122">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="bbc9d-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bbc9d-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bbc9d-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bbc9d-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="bbc9d-124">See Also</span></span>

[<span data-ttu-id="bbc9d-125">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc9d-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="bbc9d-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbc9d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
