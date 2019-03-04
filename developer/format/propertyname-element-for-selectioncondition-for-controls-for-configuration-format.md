---
title: Elemento PropertyName para SelectionCondition para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861031"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="1a8bb-102">Elemento PropertyName para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="1a8bb-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1a8bb-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1a8bb-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="1a8bb-105">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1a8bb-106">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionCondition para EntrySelectedBy para CustomEntry para configuración ( Elemento de PropertyName Format) para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1a8bb-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a8bb-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1a8bb-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a8bb-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1a8bb-108">Attributes and Elements</span></span>

<span data-ttu-id="1a8bb-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a8bb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1a8bb-110">Attributes</span></span>

<span data-ttu-id="1a8bb-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a8bb-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1a8bb-112">Child Elements</span></span>

<span data-ttu-id="1a8bb-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a8bb-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1a8bb-114">Parent Elements</span></span>

|<span data-ttu-id="1a8bb-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1a8bb-115">Element</span></span>|<span data-ttu-id="1a8bb-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="1a8bb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a8bb-117">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="1a8bb-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="1a8bb-118">Define una condición que debe cumplirse para que una definición común de control que se usará.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1a8bb-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1a8bb-119">Text Value</span></span>

<span data-ttu-id="1a8bb-120">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a8bb-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1a8bb-121">Remarks</span></span>

<span data-ttu-id="1a8bb-122">La condición de selección debe especificar un nombre de una propiedad mínimos o una secuencia de comandos, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1a8bb-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="1a8bb-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1a8bb-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a8bb-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="1a8bb-124">See Also</span></span>

[<span data-ttu-id="1a8bb-125">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="1a8bb-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="1a8bb-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a8bb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
