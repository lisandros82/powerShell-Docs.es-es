---
title: Elemento SelectionSetName para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856101"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b5682-102">Elemento SelectionSetName para EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b5682-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b5682-103">Especifica que un conjunto de .NET tipos el uso de esta entrada de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="b5682-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="b5682-104">No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="b5682-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="b5682-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento EntrySelectedBy (formato) SelectionSetName elemento de configuración EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b5682-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5682-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b5682-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5682-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b5682-107">Attributes and Elements</span></span>

<span data-ttu-id="b5682-108">Las siguientes secciones describen los atributos, elementos secundarios y elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="b5682-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5682-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5682-109">Attributes</span></span>

<span data-ttu-id="b5682-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b5682-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5682-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b5682-111">Child Elements</span></span>

<span data-ttu-id="b5682-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b5682-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5682-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b5682-113">Parent Elements</span></span>

|<span data-ttu-id="b5682-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5682-114">Element</span></span>|<span data-ttu-id="b5682-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="b5682-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5682-116">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b5682-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b5682-117">Define los tipos de .NET que usan esta entrada o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="b5682-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5682-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b5682-118">Text Value</span></span>

<span data-ttu-id="b5682-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="b5682-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5682-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b5682-120">Remarks</span></span>

<span data-ttu-id="b5682-121">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="b5682-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b5682-122">Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="b5682-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b5682-123">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para obtener una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b5682-124">Si especifica una conjunto de selección para una entrada, no se puede especificar un nombre de tipo.</span><span class="sxs-lookup"><span data-stu-id="b5682-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="b5682-125">Para obtener más información sobre cómo especificar un tipo. NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="b5682-126">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5682-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="b5682-127">See Also</span></span>

[<span data-ttu-id="b5682-128">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b5682-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="b5682-129">Definición de conjuntos de objetos para obtener una vista</span><span class="sxs-lookup"><span data-stu-id="b5682-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b5682-130">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="b5682-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b5682-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5682-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
