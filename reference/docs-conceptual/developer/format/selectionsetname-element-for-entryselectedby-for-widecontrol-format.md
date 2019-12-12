---
title: Elemento SelectionSetName para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361984"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9a60d-102">Elemento SelectionSetName para EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9a60d-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9a60d-103">Especifica un conjunto de objetos .NET para la definición.</span><span class="sxs-lookup"><span data-stu-id="9a60d-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="9a60d-104">La definición se utiliza siempre que se muestra uno de estos objetos.</span><span class="sxs-lookup"><span data-stu-id="9a60d-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="9a60d-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9a60d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a60d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9a60d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a60d-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9a60d-107">Attributes and Elements</span></span>

<span data-ttu-id="9a60d-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="9a60d-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a60d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a60d-109">Attributes</span></span>

<span data-ttu-id="9a60d-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a60d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a60d-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9a60d-111">Child Elements</span></span>

<span data-ttu-id="9a60d-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a60d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a60d-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9a60d-113">Parent Elements</span></span>

|<span data-ttu-id="9a60d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a60d-114">Element</span></span>|<span data-ttu-id="9a60d-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="9a60d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a60d-116">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9a60d-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="9a60d-117">Define los tipos de .NET que usan esta entrada ancha o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="9a60d-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a60d-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9a60d-118">Text Value</span></span>

<span data-ttu-id="9a60d-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="9a60d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a60d-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9a60d-120">Remarks</span></span>

<span data-ttu-id="9a60d-121">Cada definición debe especificar un nombre de tipo, conjunto de selección o condición de selección.</span><span class="sxs-lookup"><span data-stu-id="9a60d-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="9a60d-122">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="9a60d-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9a60d-123">Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="9a60d-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="9a60d-124">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9a60d-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9a60d-125">Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9a60d-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a60d-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="9a60d-126">See Also</span></span>

[<span data-ttu-id="9a60d-127">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="9a60d-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9a60d-128">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="9a60d-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9a60d-129">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9a60d-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="9a60d-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a60d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
