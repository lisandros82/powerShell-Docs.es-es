---
title: Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064074"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="d6c81-102">Elemento SelectionSetName para EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c81-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="d6c81-103">Especifica un conjunto de objetos de .NET para la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="d6c81-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="d6c81-104">No hay ningún límite al número de conjuntos de selección que se pueden especificar para una entrada.</span><span class="sxs-lookup"><span data-stu-id="d6c81-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="d6c81-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="d6c81-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d6c81-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c81-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6c81-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d6c81-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6c81-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d6c81-108">Attributes and Elements</span></span>

<span data-ttu-id="d6c81-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d6c81-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6c81-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6c81-110">Attributes</span></span>

<span data-ttu-id="d6c81-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d6c81-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6c81-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d6c81-112">Child Elements</span></span>

<span data-ttu-id="d6c81-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d6c81-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d6c81-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d6c81-114">Parent Elements</span></span>

|<span data-ttu-id="d6c81-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6c81-115">Element</span></span>|<span data-ttu-id="d6c81-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="d6c81-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6c81-117">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c81-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d6c81-118">Define los tipos de .NET que usan esta entrada personalizada o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="d6c81-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d6c81-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d6c81-119">Text Value</span></span>

<span data-ttu-id="d6c81-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="d6c81-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c81-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d6c81-121">Remarks</span></span>

<span data-ttu-id="d6c81-122">Cada definición de control personalizado debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="d6c81-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d6c81-123">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="d6c81-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d6c81-124">Por ejemplo, desea crear una vista de tabla y una vista de lista para el mismo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="d6c81-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d6c81-125">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d6c81-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d6c81-126">Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d6c81-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c81-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="d6c81-127">See Also</span></span>

[<span data-ttu-id="d6c81-128">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c81-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d6c81-129">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="d6c81-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d6c81-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6c81-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
