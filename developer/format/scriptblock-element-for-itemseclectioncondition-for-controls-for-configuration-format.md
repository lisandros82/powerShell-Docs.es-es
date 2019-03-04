---
title: Elemento de bloque de script para ItemSeclectionCondition para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861861"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="67136-102">Elemento ScriptBlock para ItemSelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="67136-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="67136-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="67136-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="67136-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="67136-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="67136-105">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="67136-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="67136-106">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de configuración ExpressionBinding CustomItem para los controles de configuración (formato) Elemento ItemSelectionCondition para ExpressionBinding para los controles de elemento de bloque de script de configuración (formato) para ItemSelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="67136-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67136-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="67136-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67136-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="67136-108">Attributes and Elements</span></span>

<span data-ttu-id="67136-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="67136-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67136-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="67136-110">Attributes</span></span>

<span data-ttu-id="67136-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="67136-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67136-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="67136-112">Child Elements</span></span>

<span data-ttu-id="67136-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="67136-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67136-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="67136-114">Parent Elements</span></span>

|<span data-ttu-id="67136-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="67136-115">Element</span></span>|<span data-ttu-id="67136-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="67136-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67136-117">Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="67136-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="67136-118">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="67136-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67136-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="67136-119">Text Value</span></span>

<span data-ttu-id="67136-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="67136-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="67136-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="67136-121">Remarks</span></span>

<span data-ttu-id="67136-122">Si se usa este elemento, no se puede especificar el [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="67136-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="67136-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="67136-123">See Also</span></span>

[<span data-ttu-id="67136-124">Elemento PropertyName para ItemSeclectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="67136-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="67136-125">Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="67136-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="67136-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="67136-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
