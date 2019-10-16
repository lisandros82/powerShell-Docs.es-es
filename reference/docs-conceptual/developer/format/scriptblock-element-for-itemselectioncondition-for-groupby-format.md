---
title: Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364834"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="eb0ae-102">Elemento ScriptBlock para ItemSelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="eb0ae-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="eb0ae-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="eb0ae-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="eb0ae-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="eb0ae-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para el elemento CustomItem de GroupBy (Format) para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) ItemSelectionCondition para el elemento ExpressionBinding para GroupBy (Format) elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eb0ae-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb0ae-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="eb0ae-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb0ae-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="eb0ae-108">Attributes and Elements</span></span>

<span data-ttu-id="eb0ae-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb0ae-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb0ae-110">Attributes</span></span>

<span data-ttu-id="eb0ae-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eb0ae-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="eb0ae-112">Child Elements</span></span>

<span data-ttu-id="eb0ae-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eb0ae-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="eb0ae-114">Parent Elements</span></span>

|<span data-ttu-id="eb0ae-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb0ae-115">Element</span></span>|<span data-ttu-id="eb0ae-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="eb0ae-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb0ae-117">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eb0ae-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="eb0ae-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eb0ae-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="eb0ae-119">Text Value</span></span>

<span data-ttu-id="eb0ae-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb0ae-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="eb0ae-121">Remarks</span></span>

<span data-ttu-id="eb0ae-122">Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="eb0ae-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb0ae-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="eb0ae-123">See Also</span></span>

[<span data-ttu-id="eb0ae-124">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eb0ae-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="eb0ae-125">Elemento PropertyName para ItemSelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eb0ae-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="eb0ae-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb0ae-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
