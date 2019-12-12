---
title: Elemento SelectionSetName para EntrySelectedBy para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364794"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="3bd7e-102">Elemento SelectionSetName para EntrySelectedBy for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="3bd7e-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3bd7e-103">Especifica un conjunto de tipos de .NET que usan esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="3bd7e-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3bd7e-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionSetName para EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="3bd7e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3bd7e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3bd7e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3bd7e-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3bd7e-107">Attributes and Elements</span></span>

<span data-ttu-id="3bd7e-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3bd7e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3bd7e-109">Attributes</span></span>

<span data-ttu-id="3bd7e-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="3bd7e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3bd7e-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3bd7e-111">Child Elements</span></span>

<span data-ttu-id="3bd7e-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3bd7e-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3bd7e-113">Parent Elements</span></span>

|<span data-ttu-id="3bd7e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bd7e-114">Element</span></span>|<span data-ttu-id="3bd7e-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="3bd7e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3bd7e-116">Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="3bd7e-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3bd7e-117">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3bd7e-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3bd7e-118">Text Value</span></span>

<span data-ttu-id="3bd7e-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bd7e-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3bd7e-120">Remarks</span></span>

<span data-ttu-id="3bd7e-121">Cada definición de control debe tener por lo menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3bd7e-122">Los conjuntos de selección se suelen usar cuando se desea definir un grupo de objetos que se utilizan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="3bd7e-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="3bd7e-123">Para obtener más información sobre cómo definir conjuntos de selección, consulte [definir conjuntos de selección](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3bd7e-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3bd7e-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="3bd7e-124">See Also</span></span>

[<span data-ttu-id="3bd7e-125">Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="3bd7e-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3bd7e-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bd7e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
