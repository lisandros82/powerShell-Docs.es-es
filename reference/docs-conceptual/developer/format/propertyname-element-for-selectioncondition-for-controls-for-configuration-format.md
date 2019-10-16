---
title: Elemento PropertyName para SelectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362404"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="40147-102">Elemento PropertyName para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="40147-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="40147-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="40147-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="40147-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada.</span><span class="sxs-lookup"><span data-stu-id="40147-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="40147-105">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="40147-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="40147-106">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para los controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para los controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para CustomEntry para la configuración ( Format) elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="40147-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40147-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="40147-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40147-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="40147-108">Attributes and Elements</span></span>

<span data-ttu-id="40147-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="40147-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40147-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="40147-110">Attributes</span></span>

<span data-ttu-id="40147-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="40147-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40147-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="40147-112">Child Elements</span></span>

<span data-ttu-id="40147-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="40147-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40147-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="40147-114">Parent Elements</span></span>

|<span data-ttu-id="40147-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="40147-115">Element</span></span>|<span data-ttu-id="40147-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="40147-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40147-117">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="40147-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="40147-118">Define una condición que debe existir para que se utilice una definición de control común.</span><span class="sxs-lookup"><span data-stu-id="40147-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="40147-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="40147-119">Text Value</span></span>

<span data-ttu-id="40147-120">Especifique el nombre de la propiedad .NET.</span><span class="sxs-lookup"><span data-stu-id="40147-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="40147-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="40147-121">Remarks</span></span>

<span data-ttu-id="40147-122">La condición de selección debe especificar al menos un nombre de propiedad o un script, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="40147-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="40147-123">Para obtener más información sobre cómo se pueden usar las condiciones de selección, vea [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="40147-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40147-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="40147-124">See Also</span></span>

[<span data-ttu-id="40147-125">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="40147-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="40147-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="40147-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
