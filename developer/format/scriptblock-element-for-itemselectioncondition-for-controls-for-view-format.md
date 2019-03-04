---
title: Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856741"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="4b9e2-102">Elemento ScriptBlock para ItemSelectionCondition for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="4b9e2-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="4b9e2-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4b9e2-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="4b9e2-105">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4b9e2-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato) Elemento ItemSelectionCondition de ExpressionBinding para los controles de elemento de vista (formato) ScriptBlock para ItemSelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4b9e2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b9e2-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4b9e2-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b9e2-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4b9e2-108">Attributes and Elements</span></span>

<span data-ttu-id="4b9e2-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b9e2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4b9e2-110">Attributes</span></span>

<span data-ttu-id="4b9e2-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b9e2-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4b9e2-112">Child Elements</span></span>

<span data-ttu-id="4b9e2-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4b9e2-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4b9e2-114">Parent Elements</span></span>

|<span data-ttu-id="4b9e2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b9e2-115">Element</span></span>|<span data-ttu-id="4b9e2-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="4b9e2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b9e2-117">Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4b9e2-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4b9e2-118">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4b9e2-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="4b9e2-119">Text Value</span></span>

<span data-ttu-id="4b9e2-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b9e2-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4b9e2-121">Remarks</span></span>

<span data-ttu-id="4b9e2-122">Si se usa este elemento, no se puede especificar el [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="4b9e2-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b9e2-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="4b9e2-123">See Also</span></span>

[<span data-ttu-id="4b9e2-124">Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4b9e2-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="4b9e2-125">Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4b9e2-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4b9e2-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b9e2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
