---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064669"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="1ab28-102">Elemento PropertyName para SelectionCondition for EntrySelectedBy for TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1ab28-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="1ab28-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="1ab28-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1ab28-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada de tabla.</span><span class="sxs-lookup"><span data-stu-id="1ab28-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="1ab28-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato) elemento PropertyName SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1ab28-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ab28-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1ab28-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ab28-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1ab28-107">Attributes and Elements</span></span>

<span data-ttu-id="1ab28-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1ab28-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ab28-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ab28-109">Attributes</span></span>

<span data-ttu-id="1ab28-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1ab28-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ab28-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1ab28-111">Child Elements</span></span>

<span data-ttu-id="1ab28-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1ab28-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ab28-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1ab28-113">Parent Elements</span></span>

|<span data-ttu-id="1ab28-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ab28-114">Element</span></span>|<span data-ttu-id="1ab28-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="1ab28-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ab28-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1ab28-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1ab28-117">Define la condición que debe existir para que esta entrada de tabla que se usará.</span><span class="sxs-lookup"><span data-stu-id="1ab28-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ab28-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1ab28-118">Text Value</span></span>

<span data-ttu-id="1ab28-119">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="1ab28-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ab28-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1ab28-120">Remarks</span></span>

<span data-ttu-id="1ab28-121">La condición de selección debe especificar al menos un nombre de propiedad o un bloque de script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1ab28-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="1ab28-122">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1ab28-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1ab28-123">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1ab28-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ab28-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="1ab28-124">See Also</span></span>

[<span data-ttu-id="1ab28-125">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="1ab28-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1ab28-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="1ab28-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1ab28-127">Elemento de bloque de script para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1ab28-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1ab28-128">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1ab28-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1ab28-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ab28-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
