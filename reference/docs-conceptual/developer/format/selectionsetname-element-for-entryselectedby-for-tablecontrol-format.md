---
title: Elemento SelectionSetName para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368324"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="8c109-102">Elemento SelectionSetName para EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8c109-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="8c109-103">Especifica un conjunto de tipos de .NET que usan esta entrada de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="8c109-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="8c109-104">No hay ningún límite en el número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="8c109-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="8c109-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) elemento TableRowEntry (Format) EntrySelectedBy (Format) elemento SelectionSetName para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8c109-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c109-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8c109-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c109-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8c109-107">Attributes and Elements</span></span>

<span data-ttu-id="8c109-108">En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="8c109-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c109-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c109-109">Attributes</span></span>

<span data-ttu-id="8c109-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8c109-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c109-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8c109-111">Child Elements</span></span>

<span data-ttu-id="8c109-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8c109-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8c109-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8c109-113">Parent Elements</span></span>

|<span data-ttu-id="8c109-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c109-114">Element</span></span>|<span data-ttu-id="8c109-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8c109-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c109-116">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8c109-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="8c109-117">Define los tipos .NET que usan esta entrada o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="8c109-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8c109-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8c109-118">Text Value</span></span>

<span data-ttu-id="8c109-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="8c109-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c109-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8c109-120">Remarks</span></span>

<span data-ttu-id="8c109-121">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="8c109-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8c109-122">Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="8c109-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8c109-123">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8c109-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8c109-124">Si especifica un conjunto de selección para una entrada, no puede especificar un nombre de tipo.</span><span class="sxs-lookup"><span data-stu-id="8c109-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="8c109-125">Para obtener más información sobre cómo especificar un tipo .NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="8c109-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="8c109-126">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8c109-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c109-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="8c109-127">See Also</span></span>

[<span data-ttu-id="8c109-128">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8c109-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="8c109-129">Definir conjuntos de objetos para una vista</span><span class="sxs-lookup"><span data-stu-id="8c109-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8c109-130">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="8c109-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8c109-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c109-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
