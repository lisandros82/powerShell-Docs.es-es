---
title: Elemento ExpressionBinding para CustomItem para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858301"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="0dd1f-102">Elemento ExpressionBinding para CustomItem for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="0dd1f-103">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="0dd1f-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0dd1f-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0dd1f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0dd1f-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="0dd1f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0dd1f-107">Attributes and Elements</span></span>

<span data-ttu-id="0dd1f-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0dd1f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0dd1f-109">Attributes</span></span>

<span data-ttu-id="0dd1f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0dd1f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0dd1f-111">Child Elements</span></span>

|<span data-ttu-id="0dd1f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0dd1f-112">Element</span></span>|<span data-ttu-id="0dd1f-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd1f-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="0dd1f-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0dd1f-115">Define un control que se usa este control.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="0dd1f-116">Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="0dd1f-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0dd1f-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="0dd1f-119">Elemento EnumerateCollection para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="0dd1f-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0dd1f-121">Especifica que se muestran los elementos de colecciones.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="0dd1f-122">Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="0dd1f-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0dd1f-124">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="0dd1f-125">Elemento PropertyName para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="0dd1f-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-126">Optional element.</span></span><br /><br /> <span data-ttu-id="0dd1f-127">Especifica la propiedad de .NET cuyo valor se muestra el control.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="0dd1f-128">Elemento de bloque de script para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="0dd1f-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-129">Optional element.</span></span><br /><br /> <span data-ttu-id="0dd1f-130">Especifica la secuencia de comandos cuyo valor se muestra el control.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0dd1f-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0dd1f-131">Parent Elements</span></span>

|<span data-ttu-id="0dd1f-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="0dd1f-132">Element</span></span>|<span data-ttu-id="0dd1f-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd1f-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dd1f-134">Elemento CustomItem para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="0dd1f-135">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="0dd1f-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0dd1f-136">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0dd1f-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="0dd1f-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="0dd1f-137">See Also</span></span>

[<span data-ttu-id="0dd1f-138">Elemento CustomItem para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="0dd1f-139">Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="0dd1f-140">Elemento EnumerateCollection para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="0dd1f-141">Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="0dd1f-142">Elemento PropertyName para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="0dd1f-143">Elemento de bloque de script para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="0dd1f-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="0dd1f-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0dd1f-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
