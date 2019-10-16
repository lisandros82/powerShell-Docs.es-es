---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368594"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="bc0dd-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="bc0dd-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="bc0dd-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bc0dd-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="bc0dd-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) SelectionCondition elemento for EntrySelectedBy para ListEntry (Format) elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bc0dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc0dd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bc0dd-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc0dd-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="bc0dd-107">Attributes and Elements</span></span>

<span data-ttu-id="bc0dd-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc0dd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc0dd-109">Attributes</span></span>

<span data-ttu-id="bc0dd-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc0dd-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="bc0dd-111">Child Elements</span></span>

<span data-ttu-id="bc0dd-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bc0dd-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="bc0dd-113">Parent Elements</span></span>

|<span data-ttu-id="bc0dd-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc0dd-114">Element</span></span>|<span data-ttu-id="bc0dd-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="bc0dd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc0dd-116">Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bc0dd-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="bc0dd-117">Define la condición que debe existir para que se use esta entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bc0dd-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bc0dd-118">Text Value</span></span>

<span data-ttu-id="bc0dd-119">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc0dd-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bc0dd-120">Remarks</span></span>

<span data-ttu-id="bc0dd-121">La condición de selección debe especificar al menos un nombre de script o propiedad para evaluar, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="bc0dd-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bc0dd-122">(Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para cuando se usa una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md)).</span><span class="sxs-lookup"><span data-stu-id="bc0dd-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="bc0dd-123">Para obtener más información sobre los demás componentes de una vista de lista, vea [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="bc0dd-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc0dd-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="bc0dd-124">See Also</span></span>

[<span data-ttu-id="bc0dd-125">ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="bc0dd-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="bc0dd-126">Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bc0dd-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bc0dd-127">Elemento SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bc0dd-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bc0dd-128">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="bc0dd-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bc0dd-129">Definir condiciones para cuando se utiliza una entrada de vista o un elemento</span><span class="sxs-lookup"><span data-stu-id="bc0dd-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bc0dd-130">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc0dd-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
