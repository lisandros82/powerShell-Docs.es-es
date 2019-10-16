---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368584"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="de18b-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de18b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="de18b-103">Especifica el bloque de script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="de18b-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="de18b-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa la entrada de la tabla.</span><span class="sxs-lookup"><span data-stu-id="de18b-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="de18b-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format) elemento ScriptBlock para SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de18b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de18b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="de18b-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de18b-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="de18b-107">Attributes and Elements</span></span>

<span data-ttu-id="de18b-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="de18b-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de18b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="de18b-109">Attributes</span></span>

<span data-ttu-id="de18b-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="de18b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de18b-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="de18b-111">Child Elements</span></span>

<span data-ttu-id="de18b-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="de18b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de18b-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="de18b-113">Parent Elements</span></span>

|<span data-ttu-id="de18b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="de18b-114">Element</span></span>|<span data-ttu-id="de18b-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="de18b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de18b-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de18b-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="de18b-117">Define la condición que debe existir para que se use esta entrada de tabla.</span><span class="sxs-lookup"><span data-stu-id="de18b-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de18b-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="de18b-118">Text Value</span></span>

<span data-ttu-id="de18b-119">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="de18b-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="de18b-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="de18b-120">Remarks</span></span>

<span data-ttu-id="de18b-121">La condición de selección debe especificar al menos un bloque de script o un nombre de propiedad, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="de18b-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="de18b-122">Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="de18b-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="de18b-123">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="de18b-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de18b-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="de18b-124">See Also</span></span>

[<span data-ttu-id="de18b-125">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="de18b-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="de18b-126">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="de18b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="de18b-127">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de18b-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="de18b-128">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de18b-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="de18b-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de18b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
