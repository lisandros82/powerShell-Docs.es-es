---
title: Elemento ItemSelectionCondition para ExpressionBinding para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362944"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="b3a8e-102">Elemento ItemSelectionCondition para ExpressionBinding for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="b3a8e-103">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b3a8e-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b3a8e-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format) Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3a8e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b3a8e-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b3a8e-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b3a8e-107">Attributes and Elements</span></span>

<span data-ttu-id="b3a8e-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3a8e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b3a8e-109">Attributes</span></span>

<span data-ttu-id="b3a8e-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3a8e-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b3a8e-111">Child Elements</span></span>

|<span data-ttu-id="b3a8e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b3a8e-112">Element</span></span>|<span data-ttu-id="b3a8e-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="b3a8e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3a8e-114">Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="b3a8e-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b3a8e-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b3a8e-117">Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="b3a8e-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b3a8e-119">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b3a8e-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b3a8e-120">Parent Elements</span></span>

|<span data-ttu-id="b3a8e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b3a8e-121">Element</span></span>|<span data-ttu-id="b3a8e-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="b3a8e-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3a8e-123">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b3a8e-124">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3a8e-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b3a8e-125">Remarks</span></span>

<span data-ttu-id="b3a8e-126">Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b3a8e-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3a8e-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="b3a8e-127">See Also</span></span>

[<span data-ttu-id="b3a8e-128">Elemento PropertyName para ItemSelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b3a8e-129">Elemento ScriptBlock para ItemSelectionCondition para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b3a8e-130">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3a8e-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b3a8e-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3a8e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
