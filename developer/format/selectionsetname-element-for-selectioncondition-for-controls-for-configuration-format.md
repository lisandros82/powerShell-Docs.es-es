---
title: Elemento SelectionSetName para SelectionCondition para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858141"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="26022-102">Elemento SelectionSetName para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="26022-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="26022-103">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="26022-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="26022-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de este control.</span><span class="sxs-lookup"><span data-stu-id="26022-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="26022-105">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="26022-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="26022-106">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para los controles para Elemento de configuración (formato) CustomEntry para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionCondition para EntrySelectedBy para los controles para Elemento de configuración (formato) SelectionSetName para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="26022-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26022-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="26022-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26022-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="26022-108">Attributes and Elements</span></span>

<span data-ttu-id="26022-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="26022-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26022-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="26022-110">Attributes</span></span>

<span data-ttu-id="26022-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="26022-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26022-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="26022-112">Child Elements</span></span>

<span data-ttu-id="26022-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="26022-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26022-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="26022-114">Parent Elements</span></span>

|<span data-ttu-id="26022-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="26022-115">Element</span></span>|<span data-ttu-id="26022-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="26022-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26022-117">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="26022-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="26022-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="26022-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26022-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="26022-119">Text Value</span></span>

<span data-ttu-id="26022-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="26022-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="26022-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="26022-121">Remarks</span></span>

<span data-ttu-id="26022-122">Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="26022-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="26022-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="26022-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="26022-124">La condición de selección puede especificar un conjunto de selección o un tipo. NET, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="26022-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="26022-125">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="26022-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26022-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="26022-126">See Also</span></span>

[<span data-ttu-id="26022-127">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="26022-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="26022-128">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="26022-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="26022-129">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="26022-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="26022-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="26022-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
