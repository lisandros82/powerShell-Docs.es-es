---
title: Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064012"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="f99bc-102">Elemento SelectionSetName para EntrySelectedBy for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f99bc-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f99bc-103">Especifica un conjunto de tipos de .NET que usan esta definición del control.</span><span class="sxs-lookup"><span data-stu-id="f99bc-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="f99bc-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f99bc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f99bc-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionSetName para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f99bc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f99bc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f99bc-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f99bc-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f99bc-107">Attributes and Elements</span></span>

<span data-ttu-id="f99bc-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f99bc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f99bc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f99bc-109">Attributes</span></span>

<span data-ttu-id="f99bc-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="f99bc-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f99bc-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f99bc-111">Child Elements</span></span>

<span data-ttu-id="f99bc-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f99bc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f99bc-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f99bc-113">Parent Elements</span></span>

|<span data-ttu-id="f99bc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f99bc-114">Element</span></span>|<span data-ttu-id="f99bc-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="f99bc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f99bc-116">Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f99bc-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f99bc-117">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="f99bc-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f99bc-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f99bc-118">Text Value</span></span>

<span data-ttu-id="f99bc-119">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="f99bc-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f99bc-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f99bc-120">Remarks</span></span>

<span data-ttu-id="f99bc-121">Cada definición de control debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="f99bc-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f99bc-122">Conjuntos de selección se usan normalmente cuando desea definir un grupo de objetos que se usan en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="f99bc-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="f99bc-123">Para obtener más información acerca de cómo definir conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f99bc-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f99bc-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="f99bc-124">See Also</span></span>

[<span data-ttu-id="f99bc-125">Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f99bc-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f99bc-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f99bc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
