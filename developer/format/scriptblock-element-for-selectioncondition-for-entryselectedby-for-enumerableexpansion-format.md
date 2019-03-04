---
title: Elemento de bloque de script para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854801"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="dd8ca-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="dd8ca-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="dd8ca-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="dd8ca-104">Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración (elemento) SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para Elemento de bloque de script EnumerableExpansion (formato) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="dd8ca-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd8ca-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dd8ca-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd8ca-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="dd8ca-106">Attributes and Elements</span></span>

<span data-ttu-id="dd8ca-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd8ca-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd8ca-108">Attributes</span></span>

<span data-ttu-id="dd8ca-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd8ca-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="dd8ca-110">Child Elements</span></span>

<span data-ttu-id="dd8ca-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd8ca-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="dd8ca-112">Parent Elements</span></span>

|<span data-ttu-id="dd8ca-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd8ca-113">Element</span></span>|<span data-ttu-id="dd8ca-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="dd8ca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd8ca-115">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="dd8ca-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dd8ca-116">Define la condición que debe existir para expandir los objetos de la colección de esta definición.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd8ca-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="dd8ca-117">Text Value</span></span>

<span data-ttu-id="dd8ca-118">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd8ca-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="dd8ca-119">Remarks</span></span>

<span data-ttu-id="dd8ca-120">La condición de selección debe especificar al menos un nombre de secuencia de comandos o una propiedad para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="dd8ca-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="dd8ca-121">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dd8ca-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd8ca-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="dd8ca-122">See Also</span></span>

[<span data-ttu-id="dd8ca-123">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="dd8ca-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dd8ca-124">Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="dd8ca-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="dd8ca-125">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="dd8ca-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="dd8ca-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd8ca-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
