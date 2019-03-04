---
title: Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861691"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="95a7f-102">Elemento ItemSelectionCondition para ExpressionBinding for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="95a7f-103">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="95a7f-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="95a7f-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="95a7f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="95a7f-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de configuración ExpressionBinding CustomItem para los controles de configuración (formato) Elemento ItemSelectionCondition para ExpressionBinding para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95a7f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="95a7f-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95a7f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="95a7f-107">Attributes and Elements</span></span>

<span data-ttu-id="95a7f-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="95a7f-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95a7f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="95a7f-109">Attributes</span></span>

<span data-ttu-id="95a7f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="95a7f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95a7f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="95a7f-111">Child Elements</span></span>

|<span data-ttu-id="95a7f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="95a7f-112">Element</span></span>|<span data-ttu-id="95a7f-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="95a7f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95a7f-114">Elemento PropertyName para ItemSelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="95a7f-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95a7f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="95a7f-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="95a7f-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="95a7f-117">Elemento de bloque de script para ItemSelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="95a7f-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95a7f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="95a7f-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="95a7f-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95a7f-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="95a7f-120">Parent Elements</span></span>

|<span data-ttu-id="95a7f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="95a7f-121">Element</span></span>|<span data-ttu-id="95a7f-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="95a7f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95a7f-123">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="95a7f-124">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="95a7f-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95a7f-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="95a7f-125">Remarks</span></span>

<span data-ttu-id="95a7f-126">Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="95a7f-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="95a7f-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="95a7f-127">See Also</span></span>

[<span data-ttu-id="95a7f-128">Elemento PropertyName para ItemSelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="95a7f-129">Elemento de bloque de script para ItemSelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="95a7f-130">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="95a7f-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="95a7f-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="95a7f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
