---
title: Elemento de bloque de script para SelectionCondition para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064397"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="484c7-102">Elemento ScriptBlock para SelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="484c7-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="484c7-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="484c7-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="484c7-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="484c7-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="484c7-105">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="484c7-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="484c7-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionCondition para EntrySelectedBy para los controles de vista) Elemento de bloque de script Format) para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="484c7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="484c7-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="484c7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="484c7-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="484c7-108">Attributes and Elements</span></span>

<span data-ttu-id="484c7-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="484c7-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="484c7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="484c7-110">Attributes</span></span>

<span data-ttu-id="484c7-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="484c7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="484c7-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="484c7-112">Child Elements</span></span>

<span data-ttu-id="484c7-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="484c7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="484c7-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="484c7-114">Parent Elements</span></span>

|<span data-ttu-id="484c7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="484c7-115">Element</span></span>|<span data-ttu-id="484c7-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="484c7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="484c7-117">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="484c7-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="484c7-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="484c7-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="484c7-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="484c7-119">Text Value</span></span>

<span data-ttu-id="484c7-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="484c7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="484c7-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="484c7-121">Remarks</span></span>

<span data-ttu-id="484c7-122">La condición de selección debe especificar un nombre de la secuencia de comandos o la propiedad del uno menor para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="484c7-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="484c7-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="484c7-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="484c7-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="484c7-124">See Also</span></span>

[<span data-ttu-id="484c7-125">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="484c7-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="484c7-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="484c7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
