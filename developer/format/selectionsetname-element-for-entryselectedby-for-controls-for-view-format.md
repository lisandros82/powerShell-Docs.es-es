---
title: Elemento SelectionSetName para EntrySelectedBy para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861001"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="685d3-102">Elemento SelectionSetName para EntrySelectedBy for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="685d3-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="685d3-103">Especifica un conjunto de tipos de .NET que usan esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="685d3-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="685d3-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="685d3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="685d3-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionSetName para EntrySelectedBy para los controles de vista) Formato)</span><span class="sxs-lookup"><span data-stu-id="685d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="685d3-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="685d3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="685d3-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="685d3-107">Attributes and Elements</span></span>

<span data-ttu-id="685d3-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="685d3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="685d3-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="685d3-109">Attributes</span></span>

<span data-ttu-id="685d3-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="685d3-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="685d3-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="685d3-111">Child Elements</span></span>

<span data-ttu-id="685d3-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="685d3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="685d3-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="685d3-113">Parent Elements</span></span>

|<span data-ttu-id="685d3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="685d3-114">Element</span></span>|<span data-ttu-id="685d3-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="685d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="685d3-116">Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="685d3-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="685d3-117">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="685d3-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="685d3-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="685d3-118">Text Value</span></span>

<span data-ttu-id="685d3-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="685d3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="685d3-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="685d3-120">Remarks</span></span>

<span data-ttu-id="685d3-121">Cada definición de control debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="685d3-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="685d3-122">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="685d3-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="685d3-123">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="685d3-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="685d3-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="685d3-124">See Also</span></span>

[<span data-ttu-id="685d3-125">Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="685d3-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="685d3-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="685d3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
