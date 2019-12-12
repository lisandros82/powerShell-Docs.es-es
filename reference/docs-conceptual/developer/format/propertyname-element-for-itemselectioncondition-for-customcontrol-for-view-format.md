---
title: Elemento PropertyName para ItemSelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362444"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="2f5ee-102">Elemento PropertyName para ItemSelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="2f5ee-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="2f5ee-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="2f5ee-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2f5ee-105">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2f5ee-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para View (Format) elemento ExpressionBinding para CustomItem para CustomControl para la vista (Format) elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para el elemento PropertyName for View (Format) para ItemSelectionCondition para CustomControl para View (Format</span><span class="sxs-lookup"><span data-stu-id="2f5ee-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="2f5ee-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2f5ee-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f5ee-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2f5ee-108">Attributes and Elements</span></span>

<span data-ttu-id="2f5ee-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f5ee-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2f5ee-110">Attributes</span></span>

<span data-ttu-id="2f5ee-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f5ee-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2f5ee-112">Child Elements</span></span>

<span data-ttu-id="2f5ee-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f5ee-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2f5ee-114">Parent Elements</span></span>

|<span data-ttu-id="2f5ee-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f5ee-115">Element</span></span>|<span data-ttu-id="2f5ee-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="2f5ee-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f5ee-117">Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2f5ee-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="2f5ee-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2f5ee-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="2f5ee-119">Text Value</span></span>

<span data-ttu-id="2f5ee-120">Especifique el nombre de la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f5ee-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2f5ee-121">Remarks</span></span>

<span data-ttu-id="2f5ee-122">Si se usa este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="2f5ee-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f5ee-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="2f5ee-123">See Also</span></span>

[<span data-ttu-id="2f5ee-124">Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2f5ee-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2f5ee-125">Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="2f5ee-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="2f5ee-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f5ee-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
