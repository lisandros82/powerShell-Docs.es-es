---
title: Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362074"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="9a265-102">Elemento ScriptBlock para ItemSelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="9a265-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="9a265-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="9a265-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9a265-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="9a265-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="9a265-105">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="9a265-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9a265-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para View (Format) elemento ExpressionBinding para CustomItem para CustomControl para el elemento ItemSelectionCondition de View (Format) para el enlace de expresiones para CustomControl para el elemento ScriptBlock for View (Format) para ItemSelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9a265-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a265-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9a265-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a265-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9a265-108">Attributes and Elements</span></span>

<span data-ttu-id="9a265-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="9a265-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a265-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a265-110">Attributes</span></span>

<span data-ttu-id="9a265-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a265-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a265-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9a265-112">Child Elements</span></span>

<span data-ttu-id="9a265-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a265-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a265-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9a265-114">Parent Elements</span></span>

|<span data-ttu-id="9a265-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a265-115">Element</span></span>|<span data-ttu-id="9a265-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="9a265-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a265-117">Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9a265-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="9a265-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="9a265-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a265-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9a265-119">Text Value</span></span>

<span data-ttu-id="9a265-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="9a265-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a265-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9a265-121">Remarks</span></span>

<span data-ttu-id="9a265-122">Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="9a265-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a265-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="9a265-123">See Also</span></span>

[<span data-ttu-id="9a265-124">Elemento PropertyName para ItemSelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9a265-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9a265-125">Elemento ItemSelectionCondition para el enlace de expresiones para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="9a265-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="9a265-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a265-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
