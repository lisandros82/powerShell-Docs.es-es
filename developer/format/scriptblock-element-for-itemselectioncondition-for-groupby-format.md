---
title: Elemento de bloque de script para ItemSelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860951"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="e0e6c-102">Elemento ScriptBlock para ItemSelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e0e6c-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="e0e6c-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e0e6c-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e0e6c-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e0e6c-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado de elemento de CustomItem GroupBy (formato) para CustomEntry GroupBy (formato) ExpressionBinding elemento para CustomItem para GroupBy (formato) (elemento) ItemSelectionCondition para ExpressionBinding para elemento de bloque de script GroupBy (formato) de ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e0e6c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0e6c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e0e6c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0e6c-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e0e6c-108">Attributes and Elements</span></span>

<span data-ttu-id="e0e6c-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0e6c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0e6c-110">Attributes</span></span>

<span data-ttu-id="e0e6c-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0e6c-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e0e6c-112">Child Elements</span></span>

<span data-ttu-id="e0e6c-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0e6c-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e0e6c-114">Parent Elements</span></span>

|<span data-ttu-id="e0e6c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0e6c-115">Element</span></span>|<span data-ttu-id="e0e6c-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="e0e6c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0e6c-117">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e0e6c-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="e0e6c-118">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e0e6c-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e0e6c-119">Text Value</span></span>

<span data-ttu-id="e0e6c-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0e6c-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e0e6c-121">Remarks</span></span>

<span data-ttu-id="e0e6c-122">Si se usa este elemento, no se puede especificar el [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="e0e6c-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0e6c-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="e0e6c-123">See Also</span></span>

[<span data-ttu-id="e0e6c-124">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e0e6c-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e0e6c-125">Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e0e6c-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="e0e6c-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0e6c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
