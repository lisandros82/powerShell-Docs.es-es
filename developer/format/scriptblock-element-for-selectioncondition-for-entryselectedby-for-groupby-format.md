---
title: Elemento de bloque de script para SelectionCondition para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853081"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="bfec4-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfec4-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="bfec4-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="bfec4-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bfec4-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="bfec4-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="bfec4-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="bfec4-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bfec4-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionCondition para EntrySelectedBy para elemento de bloque de script de GroupBy (formato) de SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfec4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfec4-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bfec4-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bfec4-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="bfec4-108">Attributes and Elements</span></span>

<span data-ttu-id="bfec4-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="bfec4-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfec4-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bfec4-110">Attributes</span></span>

<span data-ttu-id="bfec4-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bfec4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfec4-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="bfec4-112">Child Elements</span></span>

<span data-ttu-id="bfec4-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bfec4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bfec4-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="bfec4-114">Parent Elements</span></span>

|<span data-ttu-id="bfec4-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bfec4-115">Element</span></span>|<span data-ttu-id="bfec4-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="bfec4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfec4-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfec4-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bfec4-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="bfec4-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bfec4-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bfec4-119">Text Value</span></span>

<span data-ttu-id="bfec4-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="bfec4-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfec4-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bfec4-121">Remarks</span></span>

<span data-ttu-id="bfec4-122">La condición de selección debe especificar un nombre de la secuencia de comandos o la propiedad del uno menor para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="bfec4-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bfec4-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bfec4-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfec4-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="bfec4-124">See Also</span></span>

[<span data-ttu-id="bfec4-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfec4-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bfec4-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfec4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
