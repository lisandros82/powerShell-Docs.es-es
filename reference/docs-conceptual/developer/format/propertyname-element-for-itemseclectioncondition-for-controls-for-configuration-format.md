---
title: Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362534"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="ed625-102">Elemento PropertyName para ItemSelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="ed625-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ed625-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="ed625-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ed625-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se utiliza el control.</span><span class="sxs-lookup"><span data-stu-id="ed625-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ed625-105">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="ed625-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ed625-106">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de Configuration ExpressionBinding Element for CustomItem para los controles de configuración (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format) elemento PropertyName para ItemSeclectionCondition para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="ed625-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed625-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ed625-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed625-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ed625-108">Attributes and Elements</span></span>

<span data-ttu-id="ed625-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="ed625-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed625-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed625-110">Attributes</span></span>

<span data-ttu-id="ed625-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ed625-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed625-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ed625-112">Child Elements</span></span>

<span data-ttu-id="ed625-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ed625-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ed625-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ed625-114">Parent Elements</span></span>

|<span data-ttu-id="ed625-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed625-115">Element</span></span>|<span data-ttu-id="ed625-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="ed625-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed625-117">Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="ed625-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ed625-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="ed625-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ed625-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ed625-119">Text Value</span></span>

<span data-ttu-id="ed625-120">Especifique el nombre de la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="ed625-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed625-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ed625-121">Remarks</span></span>

<span data-ttu-id="ed625-122">Si se usa este elemento, no se puede especificar el elemento [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="ed625-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed625-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="ed625-123">See Also</span></span>

[<span data-ttu-id="ed625-124">Elemento ScriptBlock para ItemSeclectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="ed625-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ed625-125">Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="ed625-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="ed625-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed625-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
