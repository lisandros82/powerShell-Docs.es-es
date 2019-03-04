---
title: Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862751"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="87072-102">Elemento SelectionSetName para EntrySelectedBy for EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="87072-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="87072-103">Especifica el conjunto de tipos de .NET que se expanden por esta definición.</span><span class="sxs-lookup"><span data-stu-id="87072-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="87072-104">Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuración (elemento) SelectionSetName EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="87072-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87072-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="87072-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="87072-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="87072-106">Attributes and Elements</span></span>

<span data-ttu-id="87072-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="87072-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87072-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="87072-108">Attributes</span></span>

<span data-ttu-id="87072-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="87072-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87072-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="87072-110">Child Elements</span></span>

<span data-ttu-id="87072-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="87072-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87072-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="87072-112">Parent Elements</span></span>

|<span data-ttu-id="87072-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="87072-113">Element</span></span>|<span data-ttu-id="87072-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="87072-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87072-115">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="87072-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="87072-116">Define los objetos de colección de .NET que se expanden por esta definición.</span><span class="sxs-lookup"><span data-stu-id="87072-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87072-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="87072-117">Text Value</span></span>

<span data-ttu-id="87072-118">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="87072-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="87072-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="87072-119">Remarks</span></span>

<span data-ttu-id="87072-120">Cada definición debe especificar uno o más nombres de tipo, un conjunto de selección o una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="87072-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="87072-121">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="87072-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="87072-122">Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="87072-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="87072-123">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir establece de objetos para obtener una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="87072-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87072-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="87072-124">See Also</span></span>

[<span data-ttu-id="87072-125">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="87072-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="87072-126">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="87072-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="87072-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="87072-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
