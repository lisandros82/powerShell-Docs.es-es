---
title: Elemento de bloque de script para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076351"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="aadc2-102">Elemento ScriptBlock para SelectionCondition for EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="aadc2-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="aadc2-103">Especifica el bloque de script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="aadc2-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="aadc2-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la entrada de tabla.</span><span class="sxs-lookup"><span data-stu-id="aadc2-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="aadc2-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para elemento de bloque de script de TableRowEntry (formato) de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aadc2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aadc2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aadc2-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aadc2-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="aadc2-107">Attributes and Elements</span></span>

<span data-ttu-id="aadc2-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="aadc2-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aadc2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="aadc2-109">Attributes</span></span>

<span data-ttu-id="aadc2-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="aadc2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aadc2-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="aadc2-111">Child Elements</span></span>

<span data-ttu-id="aadc2-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="aadc2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aadc2-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="aadc2-113">Parent Elements</span></span>

|<span data-ttu-id="aadc2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="aadc2-114">Element</span></span>|<span data-ttu-id="aadc2-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="aadc2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aadc2-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aadc2-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="aadc2-117">Define la condición que debe existir para que esta entrada de tabla que se usará.</span><span class="sxs-lookup"><span data-stu-id="aadc2-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aadc2-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="aadc2-118">Text Value</span></span>

<span data-ttu-id="aadc2-119">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="aadc2-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="aadc2-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="aadc2-120">Remarks</span></span>

<span data-ttu-id="aadc2-121">La condición de selección debe especificar al menos un nombre de propiedad o de bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="aadc2-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="aadc2-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="aadc2-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="aadc2-123">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="aadc2-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aadc2-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="aadc2-124">See Also</span></span>

[<span data-ttu-id="aadc2-125">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="aadc2-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="aadc2-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="aadc2-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="aadc2-127">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aadc2-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="aadc2-128">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aadc2-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="aadc2-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aadc2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
