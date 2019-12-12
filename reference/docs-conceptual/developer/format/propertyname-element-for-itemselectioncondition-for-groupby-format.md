---
title: Elemento PropertyName para ItemSelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362414"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="ca5f3-102">Elemento PropertyName para ItemSelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ca5f3-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="ca5f3-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ca5f3-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ca5f3-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ca5f3-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) ItemSelectionCondition para el elemento ExpressionBinding para GroupBy (Format) PropertyName para ItemSelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ca5f3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca5f3-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ca5f3-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca5f3-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ca5f3-108">Attributes and Elements</span></span>

<span data-ttu-id="ca5f3-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca5f3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca5f3-110">Attributes</span></span>

<span data-ttu-id="ca5f3-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca5f3-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ca5f3-112">Child Elements</span></span>

<span data-ttu-id="ca5f3-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca5f3-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ca5f3-114">Parent Elements</span></span>

|<span data-ttu-id="ca5f3-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca5f3-115">Element</span></span>|<span data-ttu-id="ca5f3-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="ca5f3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca5f3-117">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ca5f3-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="ca5f3-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ca5f3-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ca5f3-119">Text Value</span></span>

<span data-ttu-id="ca5f3-120">Especifique el nombre de la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca5f3-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ca5f3-121">Remarks</span></span>

<span data-ttu-id="ca5f3-122">Si se usa este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="ca5f3-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca5f3-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="ca5f3-123">See Also</span></span>

[<span data-ttu-id="ca5f3-124">Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ca5f3-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="ca5f3-125">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ca5f3-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="ca5f3-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca5f3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
