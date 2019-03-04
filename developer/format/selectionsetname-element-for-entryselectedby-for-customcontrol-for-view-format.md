---
title: Elemento SelectionSetName para EntrySelectedBy para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855031"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="8fa0f-102">Elemento SelectionSetName para EntrySelectedBy for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="8fa0f-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="8fa0f-103">Especifica un conjunto de objetos de .NET para la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="8fa0f-104">No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="8fa0f-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry de vista (formato) del elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8fa0f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fa0f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8fa0f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8fa0f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8fa0f-107">Attributes and Elements</span></span>

<span data-ttu-id="8fa0f-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fa0f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8fa0f-109">Attributes</span></span>

<span data-ttu-id="8fa0f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fa0f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8fa0f-111">Child Elements</span></span>

<span data-ttu-id="8fa0f-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8fa0f-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8fa0f-113">Parent Elements</span></span>

|<span data-ttu-id="8fa0f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8fa0f-114">Element</span></span>|<span data-ttu-id="8fa0f-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8fa0f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fa0f-116">Elemento EntrySelectedBy para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8fa0f-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="8fa0f-117">Define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8fa0f-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8fa0f-118">Text Value</span></span>

<span data-ttu-id="8fa0f-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fa0f-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8fa0f-120">Remarks</span></span>

<span data-ttu-id="8fa0f-121">Cada entrada de control personalizado debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8fa0f-122">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8fa0f-123">Por ejemplo, es posible que desee crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="8fa0f-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8fa0f-124">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8fa0f-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8fa0f-125">Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8fa0f-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fa0f-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="8fa0f-126">See Also</span></span>

[<span data-ttu-id="8fa0f-127">Elemento EntrySelectedBy para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8fa0f-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8fa0f-128">Vista de Control personalizado</span><span class="sxs-lookup"><span data-stu-id="8fa0f-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8fa0f-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fa0f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
