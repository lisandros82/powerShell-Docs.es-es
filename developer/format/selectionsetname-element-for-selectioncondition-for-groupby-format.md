---
title: Elemento SelectionSetName para SelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856761"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="1be2b-102">Elemento SelectionSetName para SelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1be2b-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="1be2b-103">Especifica el conjunto de tipos de .NET que la condición desencadenadora.</span><span class="sxs-lookup"><span data-stu-id="1be2b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1be2b-104">Cuando cualquiera de los tipos de este conjunto está presente, se cumple la condición y el objeto se muestra mediante el uso de este control.</span><span class="sxs-lookup"><span data-stu-id="1be2b-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="1be2b-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="1be2b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1be2b-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionCondition para EntrySelectedBy para GroupBy (formato) (elemento) SelectionSetName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1be2b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1be2b-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1be2b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1be2b-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1be2b-108">Attributes and Elements</span></span>

<span data-ttu-id="1be2b-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1be2b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1be2b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1be2b-110">Attributes</span></span>

<span data-ttu-id="1be2b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1be2b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1be2b-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1be2b-112">Child Elements</span></span>

<span data-ttu-id="1be2b-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1be2b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1be2b-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1be2b-114">Parent Elements</span></span>

|<span data-ttu-id="1be2b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1be2b-115">Element</span></span>|<span data-ttu-id="1be2b-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="1be2b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1be2b-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1be2b-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1be2b-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="1be2b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1be2b-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1be2b-119">Text Value</span></span>

<span data-ttu-id="1be2b-120">Especifique el nombre del conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="1be2b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1be2b-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1be2b-121">Remarks</span></span>

<span data-ttu-id="1be2b-122">Conjuntos de selección son grupos comunes de objetos .NET que pueden usarse en cualquier vista que define el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="1be2b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1be2b-123">Para obtener más información sobre cómo crear y hacer referencia a conjuntos de selección, consulte [definir selección establece](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1be2b-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1be2b-124">Cuando se especifica este elemento, no puede especificar el [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1be2b-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="1be2b-125">Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1be2b-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1be2b-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="1be2b-126">See Also</span></span>

[<span data-ttu-id="1be2b-127">Elemento TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1be2b-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="1be2b-128">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1be2b-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1be2b-129">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="1be2b-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1be2b-130">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="1be2b-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1be2b-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1be2b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
