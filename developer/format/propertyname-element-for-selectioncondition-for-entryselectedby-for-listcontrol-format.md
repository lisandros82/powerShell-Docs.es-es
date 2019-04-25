---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064906"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="e8959-102">Elemento PropertyName para SelectionCondition for EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e8959-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="e8959-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e8959-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e8959-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="e8959-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="e8959-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuración para ListEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para ListEntry (formato) elemento PropertyName SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e8959-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8959-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e8959-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8959-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e8959-107">Attributes and Elements</span></span>

<span data-ttu-id="e8959-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e8959-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8959-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e8959-109">Attributes</span></span>

<span data-ttu-id="e8959-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e8959-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8959-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e8959-111">Child Elements</span></span>

<span data-ttu-id="e8959-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e8959-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e8959-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e8959-113">Parent Elements</span></span>

|<span data-ttu-id="e8959-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8959-114">Element</span></span>|<span data-ttu-id="e8959-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="e8959-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8959-116">Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e8959-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e8959-117">Define la condición que debe existir para que esta entrada de lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="e8959-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e8959-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e8959-118">Text Value</span></span>

<span data-ttu-id="e8959-119">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="e8959-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8959-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e8959-120">Remarks</span></span>

<span data-ttu-id="e8959-121">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="e8959-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="e8959-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e8959-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e8959-123">Para obtener más información sobre otros componentes de una vista de lista, consulte [Crear vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e8959-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8959-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="e8959-124">See Also</span></span>

[<span data-ttu-id="e8959-125">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="e8959-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e8959-126">Definir condiciones para los datos cuando se muestra.</span><span class="sxs-lookup"><span data-stu-id="e8959-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e8959-127">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e8959-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="e8959-128">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e8959-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e8959-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8959-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
