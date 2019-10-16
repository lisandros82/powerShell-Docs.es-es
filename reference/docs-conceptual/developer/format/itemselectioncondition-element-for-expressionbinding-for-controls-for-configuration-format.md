---
title: Elemento ItemSelectionCondition para ExpressionBinding para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362924"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="a2052-102">Elemento ItemSelectionCondition para ExpressionBinding for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="a2052-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a2052-103">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="a2052-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a2052-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="a2052-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a2052-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de Configuration ExpressionBinding Element for CustomItem para los controles de configuración (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a2052-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a2052-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2052-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="a2052-107">Attributes and Elements</span></span>

<span data-ttu-id="a2052-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="a2052-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2052-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a2052-109">Attributes</span></span>

<span data-ttu-id="a2052-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="a2052-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2052-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="a2052-111">Child Elements</span></span>

|<span data-ttu-id="a2052-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a2052-112">Element</span></span>|<span data-ttu-id="a2052-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2052-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2052-114">Elemento PropertyName para ItemSelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="a2052-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a2052-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a2052-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="a2052-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a2052-117">Elemento ScriptBlock para ItemSelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="a2052-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a2052-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a2052-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="a2052-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a2052-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="a2052-120">Parent Elements</span></span>

|<span data-ttu-id="a2052-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a2052-121">Element</span></span>|<span data-ttu-id="a2052-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2052-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2052-123">Elemento ExpressionBinding de CustomItem para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="a2052-124">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="a2052-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2052-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a2052-125">Remarks</span></span>

<span data-ttu-id="a2052-126">Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="a2052-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2052-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="a2052-127">See Also</span></span>

[<span data-ttu-id="a2052-128">Elemento PropertyName para ItemSelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="a2052-129">Elemento ScriptBlock para ItemSelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="a2052-130">Elemento ExpressionBinding de CustomItem para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="a2052-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="a2052-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2052-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
