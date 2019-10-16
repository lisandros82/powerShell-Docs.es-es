---
title: Elemento ExpressionBinding para CustomItem para controles para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363784"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="b51a7-102">Elemento ExpressionBinding para CustomItem for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="b51a7-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="b51a7-103">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="b51a7-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b51a7-104">Este elemento se utiliza al definir controles que se pueden usar en una vista.</span><span class="sxs-lookup"><span data-stu-id="b51a7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b51a7-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento control (Format) elemento control para controles del elemento CustomControl View (Format) para el control de los controles del elemento CustomEntries View (Format) para CustomControl para el elemento CustomEntry de View (Format) para CustomEntries para los controles del elemento CustomItem View (Format) para CustomEntry para los controles del elemento ExpressionBinding View (Format) para CustomItem para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b51a7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b51a7-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b51a7-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b51a7-107">Attributes and Elements</span></span>

<span data-ttu-id="b51a7-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="b51a7-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b51a7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b51a7-109">Attributes</span></span>

<span data-ttu-id="b51a7-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b51a7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b51a7-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b51a7-111">Child Elements</span></span>

|<span data-ttu-id="b51a7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b51a7-112">Element</span></span>|<span data-ttu-id="b51a7-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="b51a7-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b51a7-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b51a7-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b51a7-115">Define un control utilizado por este control.</span><span class="sxs-lookup"><span data-stu-id="b51a7-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b51a7-116">Elemento CustomControlName para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="b51a7-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b51a7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b51a7-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="b51a7-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="b51a7-119">Elemento EnumerateCollection para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="b51a7-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b51a7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b51a7-121">Especifica que se muestran los elementos de las colecciones.</span><span class="sxs-lookup"><span data-stu-id="b51a7-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b51a7-122">Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="b51a7-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b51a7-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b51a7-124">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="b51a7-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b51a7-125">Elemento PropertyName para ExpressionBinding para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="b51a7-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b51a7-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b51a7-127">Especifica la propiedad de .NET cuyo valor muestra el control.</span><span class="sxs-lookup"><span data-stu-id="b51a7-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b51a7-128">Elemento ScriptBlock para ExpressionBinding para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="b51a7-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b51a7-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b51a7-130">Especifica el script cuyo valor muestra el control.</span><span class="sxs-lookup"><span data-stu-id="b51a7-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b51a7-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b51a7-131">Parent Elements</span></span>

|<span data-ttu-id="b51a7-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="b51a7-132">Element</span></span>|<span data-ttu-id="b51a7-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="b51a7-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b51a7-134">Elemento CustomItem para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="b51a7-135">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="b51a7-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b51a7-136">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b51a7-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b51a7-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="b51a7-137">See Also</span></span>

[<span data-ttu-id="b51a7-138">Elemento CustomItem para CustomEntry para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="b51a7-139">Elemento CustomControlName para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b51a7-140">Elemento EnumerateCollection para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b51a7-141">Elemento ItemSelectionCondition de ExpressionBinding para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b51a7-142">Elemento PropertyName para ExpressionBinding para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b51a7-143">Elemento ScriptBlock para ExpressionBinding para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="b51a7-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b51a7-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b51a7-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
