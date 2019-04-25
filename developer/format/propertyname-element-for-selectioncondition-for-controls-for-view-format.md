---
title: Elemento PropertyName para SelectionCondition para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065026"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="92245-102">Elemento PropertyName para SelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="92245-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="92245-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="92245-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="92245-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la entrada.</span><span class="sxs-lookup"><span data-stu-id="92245-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="92245-105">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="92245-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="92245-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de elemento de vista (formato) CustomEntry para CustomEntries para los controles de elemento de vista (formato) EntrySelectedBy para CustomEntry para los controles de elemento de vista (formato) SelectionCondition para EntrySelectedBy para los controles de vista) Elemento de PropertyName Format) para SelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="92245-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92245-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="92245-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92245-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="92245-108">Attributes and Elements</span></span>

<span data-ttu-id="92245-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="92245-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92245-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="92245-110">Attributes</span></span>

<span data-ttu-id="92245-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="92245-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92245-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="92245-112">Child Elements</span></span>

<span data-ttu-id="92245-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="92245-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92245-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="92245-114">Parent Elements</span></span>

|<span data-ttu-id="92245-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="92245-115">Element</span></span>|<span data-ttu-id="92245-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="92245-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92245-117">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="92245-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="92245-118">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="92245-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92245-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="92245-119">Text Value</span></span>

<span data-ttu-id="92245-120">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="92245-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="92245-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="92245-121">Remarks</span></span>

<span data-ttu-id="92245-122">La condición de selección debe especificar un nombre de una propiedad mínimos o una secuencia de comandos, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="92245-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="92245-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="92245-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92245-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="92245-124">See Also</span></span>

[<span data-ttu-id="92245-125">Elemento SelectionCondition para EntrySelectedBy para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="92245-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="92245-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="92245-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
