---
title: Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368334"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="8eab4-102">Elemento SelectionSetName para EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="8eab4-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="8eab4-103">Especifica el conjunto de tipos de .NET que se expanden con esta definición.</span><span class="sxs-lookup"><span data-stu-id="8eab4-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="8eab4-104">Elemento de configuración (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) elemento EntrySelectedBy para EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="8eab4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8eab4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8eab4-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8eab4-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8eab4-106">Attributes and Elements</span></span>

<span data-ttu-id="8eab4-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="8eab4-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8eab4-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8eab4-108">Attributes</span></span>

<span data-ttu-id="8eab4-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8eab4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8eab4-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8eab4-110">Child Elements</span></span>

<span data-ttu-id="8eab4-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8eab4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8eab4-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8eab4-112">Parent Elements</span></span>

|<span data-ttu-id="8eab4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8eab4-113">Element</span></span>|<span data-ttu-id="8eab4-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="8eab4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eab4-115">Elemento EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="8eab4-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="8eab4-116">Define los objetos de la colección de .NET que se expanden con esta definición.</span><span class="sxs-lookup"><span data-stu-id="8eab4-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8eab4-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8eab4-117">Text Value</span></span>

<span data-ttu-id="8eab4-118">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="8eab4-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8eab4-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8eab4-119">Remarks</span></span>

<span data-ttu-id="8eab4-120">Cada definición debe especificar uno o más nombres de tipo, un conjunto de selección o una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="8eab4-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="8eab4-121">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="8eab4-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8eab4-122">Por ejemplo, puede que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="8eab4-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8eab4-123">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de objetos para una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8eab4-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8eab4-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="8eab4-124">See Also</span></span>

[<span data-ttu-id="8eab4-125">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="8eab4-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8eab4-126">Elemento EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="8eab4-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="8eab4-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8eab4-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
