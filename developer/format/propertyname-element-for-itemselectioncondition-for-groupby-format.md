---
title: Elemento PropertyName para ItemSelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858271"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="1d6ce-102">Elemento PropertyName para ItemSelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1d6ce-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="1d6ce-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1d6ce-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="1d6ce-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1d6ce-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado de elemento de CustomItem GroupBy (formato) para CustomEntry GroupBy (formato) ExpressionBinding elemento para CustomItem para GroupBy (formato) (elemento) ItemSelectionCondition para ExpressionBinding elemento PropertyName de GroupBy (formato) para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1d6ce-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d6ce-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1d6ce-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d6ce-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1d6ce-108">Attributes and Elements</span></span>

<span data-ttu-id="1d6ce-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d6ce-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d6ce-110">Attributes</span></span>

<span data-ttu-id="1d6ce-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d6ce-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1d6ce-112">Child Elements</span></span>

<span data-ttu-id="1d6ce-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d6ce-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1d6ce-114">Parent Elements</span></span>

|<span data-ttu-id="1d6ce-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d6ce-115">Element</span></span>|<span data-ttu-id="1d6ce-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="1d6ce-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d6ce-117">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1d6ce-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="1d6ce-118">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d6ce-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1d6ce-119">Text Value</span></span>

<span data-ttu-id="1d6ce-120">Especifique el nombre de la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d6ce-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1d6ce-121">Remarks</span></span>

<span data-ttu-id="1d6ce-122">Si se usa este elemento, no se puede especificar el [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="1d6ce-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d6ce-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="1d6ce-123">See Also</span></span>

[<span data-ttu-id="1d6ce-124">Elemento de bloque de script para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1d6ce-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="1d6ce-125">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="1d6ce-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1d6ce-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d6ce-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
