---
title: Elemento SelectionSetName para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856801"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="42808-102">Elemento SelectionSetName para EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="42808-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="42808-103">Especifica un conjunto de objetos de .NET para la definición.</span><span class="sxs-lookup"><span data-stu-id="42808-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="42808-104">La definición se usa siempre que se muestra uno de estos objetos.</span><span class="sxs-lookup"><span data-stu-id="42808-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="42808-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionSetName (elemento) para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="42808-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42808-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="42808-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="42808-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="42808-107">Attributes and Elements</span></span>

<span data-ttu-id="42808-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="42808-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42808-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="42808-109">Attributes</span></span>

<span data-ttu-id="42808-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="42808-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42808-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="42808-111">Child Elements</span></span>

<span data-ttu-id="42808-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="42808-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42808-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="42808-113">Parent Elements</span></span>

|<span data-ttu-id="42808-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="42808-114">Element</span></span>|<span data-ttu-id="42808-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="42808-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42808-116">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="42808-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="42808-117">Define los tipos de .NET que usan esta entrada del ancha o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="42808-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42808-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="42808-118">Text Value</span></span>

<span data-ttu-id="42808-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="42808-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="42808-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="42808-120">Remarks</span></span>

<span data-ttu-id="42808-121">Cada definición debe especificar un nombre de tipo, conjunto de selección o condición de selección.</span><span class="sxs-lookup"><span data-stu-id="42808-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="42808-122">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="42808-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="42808-123">Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="42808-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="42808-124">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir establece de objetos para obtener una vista](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="42808-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="42808-125">Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="42808-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42808-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="42808-126">See Also</span></span>

[<span data-ttu-id="42808-127">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="42808-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="42808-128">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="42808-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="42808-129">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="42808-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="42808-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="42808-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
