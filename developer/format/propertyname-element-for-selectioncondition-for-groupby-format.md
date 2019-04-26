---
title: Elemento PropertyName para SelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064822"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="0f653-102">Elemento PropertyName para SelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0f653-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0f653-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="0f653-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0f653-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="0f653-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="0f653-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="0f653-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0f653-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionCondition para EntrySelectedBy elemento PropertyName de GroupBy (formato) para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0f653-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f653-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0f653-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f653-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0f653-108">Attributes and Elements</span></span>

<span data-ttu-id="0f653-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0f653-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f653-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f653-110">Attributes</span></span>

<span data-ttu-id="0f653-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0f653-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f653-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0f653-112">Child Elements</span></span>

<span data-ttu-id="0f653-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0f653-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f653-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0f653-114">Parent Elements</span></span>

|<span data-ttu-id="0f653-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f653-115">Element</span></span>|<span data-ttu-id="0f653-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="0f653-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f653-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0f653-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0f653-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="0f653-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f653-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="0f653-119">Text Value</span></span>

<span data-ttu-id="0f653-120">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="0f653-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f653-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0f653-121">Remarks</span></span>

<span data-ttu-id="0f653-122">La condición de selección debe especificar un nombre de una propiedad mínimos o una secuencia de comandos, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="0f653-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="0f653-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0f653-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f653-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="0f653-124">See Also</span></span>

[<span data-ttu-id="0f653-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0f653-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0f653-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f653-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
