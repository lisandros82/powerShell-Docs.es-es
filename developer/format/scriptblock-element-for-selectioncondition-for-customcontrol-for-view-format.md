---
title: Elemento de bloque de script para SelectionCondition para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064567"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="93727-102">Elemento ScriptBlock para SelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="93727-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="93727-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="93727-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="93727-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="93727-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="93727-105">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="93727-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="93727-106">Configuración (formato) elemento ViewDefinitions (formato) Vista (formato) del elemento control personalizado elemento de vista (formato) del elemento CustomEntries para el control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para el control personalizado para la vista ( Elemento de formato) CustomItem para CustomEntry para el control personalizado de vista (formato) del elemento SelectionCondition para EntrySelectedBy para el control personalizado de vista (formato) del elemento ScriptBlock para SelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="93727-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93727-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="93727-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93727-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="93727-108">Attributes and Elements</span></span>

<span data-ttu-id="93727-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="93727-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93727-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="93727-110">Attributes</span></span>

<span data-ttu-id="93727-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="93727-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93727-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="93727-112">Child Elements</span></span>

<span data-ttu-id="93727-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="93727-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="93727-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="93727-114">Parent Elements</span></span>

|<span data-ttu-id="93727-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="93727-115">Element</span></span>|<span data-ttu-id="93727-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="93727-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93727-117">Elemento SelectionCondition para EntrySelectedBy para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="93727-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="93727-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="93727-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="93727-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="93727-119">Text Value</span></span>

<span data-ttu-id="93727-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="93727-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="93727-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="93727-121">Remarks</span></span>

<span data-ttu-id="93727-122">La condición de selección debe especificar un nombre de la secuencia de comandos o la propiedad del uno menor para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="93727-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="93727-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="93727-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93727-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="93727-124">See Also</span></span>

[<span data-ttu-id="93727-125">Elemento SelectionCondition para EntrySelectedBy para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="93727-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="93727-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="93727-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
