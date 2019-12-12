---
title: Elemento ScriptBlock para ItemSeclectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362124"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="fa0ed-102">Elemento ScriptBlock para ItemSelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="fa0ed-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fa0ed-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fa0ed-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="fa0ed-105">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fa0ed-106">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de Configuration ExpressionBinding Element for CustomItem para los controles de configuración (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format) elemento ScriptBlock para ItemSelectionCondition para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="fa0ed-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa0ed-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fa0ed-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa0ed-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fa0ed-108">Attributes and Elements</span></span>

<span data-ttu-id="fa0ed-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa0ed-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fa0ed-110">Attributes</span></span>

<span data-ttu-id="fa0ed-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa0ed-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fa0ed-112">Child Elements</span></span>

<span data-ttu-id="fa0ed-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fa0ed-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fa0ed-114">Parent Elements</span></span>

|<span data-ttu-id="fa0ed-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa0ed-115">Element</span></span>|<span data-ttu-id="fa0ed-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="fa0ed-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa0ed-117">Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="fa0ed-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="fa0ed-118">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fa0ed-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fa0ed-119">Text Value</span></span>

<span data-ttu-id="fa0ed-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa0ed-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fa0ed-121">Remarks</span></span>

<span data-ttu-id="fa0ed-122">Si se usa este elemento, no se puede especificar el elemento [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa0ed-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="fa0ed-123">See Also</span></span>

[<span data-ttu-id="fa0ed-124">Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="fa0ed-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa0ed-125">Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="fa0ed-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="fa0ed-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa0ed-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
