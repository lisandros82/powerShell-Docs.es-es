---
title: Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364924"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="fc095-102">Elemento ScriptBlock para ItemSelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="fc095-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="fc095-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="fc095-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fc095-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="fc095-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="fc095-105">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="fc095-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="fc095-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles para el elemento ScriptBlock de View (Format) para ItemSelectionCondition para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="fc095-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc095-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fc095-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc095-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fc095-108">Attributes and Elements</span></span>

<span data-ttu-id="fc095-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="fc095-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc095-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc095-110">Attributes</span></span>

<span data-ttu-id="fc095-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fc095-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc095-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fc095-112">Child Elements</span></span>

<span data-ttu-id="fc095-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fc095-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc095-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fc095-114">Parent Elements</span></span>

|<span data-ttu-id="fc095-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc095-115">Element</span></span>|<span data-ttu-id="fc095-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="fc095-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc095-117">Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="fc095-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="fc095-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="fc095-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc095-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fc095-119">Text Value</span></span>

<span data-ttu-id="fc095-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="fc095-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc095-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fc095-121">Remarks</span></span>

<span data-ttu-id="fc095-122">Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="fc095-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc095-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="fc095-123">See Also</span></span>

[<span data-ttu-id="fc095-124">Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="fc095-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="fc095-125">Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="fc095-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="fc095-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc095-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
