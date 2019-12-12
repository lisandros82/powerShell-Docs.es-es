---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361474"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="261d5-102">Elemento TypeName para SelectionCondition for EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="261d5-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="261d5-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="261d5-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="261d5-104">Cuando este tipo está presente, se cumple la condición y se usa la fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="261d5-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="261d5-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy para TableRowEntry (Format) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format) elemento TypeName para SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="261d5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="261d5-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="261d5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="261d5-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="261d5-107">Attributes and Elements</span></span>

<span data-ttu-id="261d5-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="261d5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="261d5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="261d5-109">Attributes</span></span>

<span data-ttu-id="261d5-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="261d5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="261d5-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="261d5-111">Child Elements</span></span>

<span data-ttu-id="261d5-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="261d5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="261d5-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="261d5-113">Parent Elements</span></span>

|<span data-ttu-id="261d5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="261d5-114">Element</span></span>|<span data-ttu-id="261d5-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="261d5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="261d5-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="261d5-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="261d5-117">Define la condición que debe existir para que se use esta fila de tabla.</span><span class="sxs-lookup"><span data-stu-id="261d5-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="261d5-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="261d5-118">Text Value</span></span>

<span data-ttu-id="261d5-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="261d5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="261d5-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="261d5-120">Remarks</span></span>

<span data-ttu-id="261d5-121">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="261d5-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="261d5-122">Para obtener más información sobre cómo usar las condiciones de selección, vea [definir condiciones para cuando se utiliza una entrada de vista o un elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="261d5-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="261d5-123">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="261d5-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="261d5-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="261d5-124">See Also</span></span>

[<span data-ttu-id="261d5-125">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="261d5-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="261d5-126">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="261d5-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="261d5-127">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="261d5-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="261d5-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="261d5-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="261d5-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="261d5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
