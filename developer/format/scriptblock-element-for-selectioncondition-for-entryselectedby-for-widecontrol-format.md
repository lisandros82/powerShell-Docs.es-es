---
title: Elemento de bloque de script para SelectionCondition para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862951"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="abec4-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="abec4-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="abec4-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="abec4-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="abec4-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se utiliza la definición de la entrada ancho.</span><span class="sxs-lookup"><span data-stu-id="abec4-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="abec4-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para elemento de bloque de script de WideEntry (formato) de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="abec4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="abec4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="abec4-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abec4-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="abec4-107">Attributes and Elements</span></span>

<span data-ttu-id="abec4-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="abec4-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="abec4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="abec4-109">Attributes</span></span>

<span data-ttu-id="abec4-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="abec4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="abec4-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="abec4-111">Child Elements</span></span>

<span data-ttu-id="abec4-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="abec4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="abec4-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="abec4-113">Parent Elements</span></span>

|<span data-ttu-id="abec4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="abec4-114">Element</span></span>|<span data-ttu-id="abec4-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="abec4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="abec4-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="abec4-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="abec4-117">Define la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="abec4-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="abec4-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="abec4-118">Text Value</span></span>

<span data-ttu-id="abec4-119">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="abec4-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="abec4-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="abec4-120">Remarks</span></span>

<span data-ttu-id="abec4-121">La condición de selección debe especificar al menos un nombre de secuencia de comandos o una propiedad para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="abec4-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="abec4-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="abec4-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="abec4-123">Para obtener más información sobre otros componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="abec4-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="abec4-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="abec4-124">See Also</span></span>

[<span data-ttu-id="abec4-125">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="abec4-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="abec4-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="abec4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="abec4-127">Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="abec4-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="abec4-128">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="abec4-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="abec4-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="abec4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
