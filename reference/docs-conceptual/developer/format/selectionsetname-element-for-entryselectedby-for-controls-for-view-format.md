---
title: Elemento SelectionSetName para EntrySelectedBy para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368354"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="e790d-102">Elemento SelectionSetName para EntrySelectedBy for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="e790d-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="e790d-103">Especifica un conjunto de tipos de .NET que usan esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="e790d-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e790d-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="e790d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e790d-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para los controles del elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento EntrySelectedBy View (Format) para CustomEntry para los controles del elemento SelectionSetName View (Format) para EntrySelectedBy para los controles de la vista ( Aplique</span><span class="sxs-lookup"><span data-stu-id="e790d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e790d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e790d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e790d-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e790d-107">Attributes and Elements</span></span>

<span data-ttu-id="e790d-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="e790d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e790d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e790d-109">Attributes</span></span>

<span data-ttu-id="e790d-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="e790d-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e790d-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e790d-111">Child Elements</span></span>

<span data-ttu-id="e790d-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e790d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e790d-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e790d-113">Parent Elements</span></span>

|<span data-ttu-id="e790d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e790d-114">Element</span></span>|<span data-ttu-id="e790d-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="e790d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e790d-116">Elemento EntrySelectedBy para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="e790d-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e790d-117">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="e790d-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e790d-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e790d-118">Text Value</span></span>

<span data-ttu-id="e790d-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="e790d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e790d-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e790d-120">Remarks</span></span>

<span data-ttu-id="e790d-121">Cada definición de control debe tener por lo menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="e790d-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e790d-122">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="e790d-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e790d-123">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e790d-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e790d-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="e790d-124">See Also</span></span>

[<span data-ttu-id="e790d-125">Elemento EntrySelectedBy para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="e790d-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="e790d-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e790d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
