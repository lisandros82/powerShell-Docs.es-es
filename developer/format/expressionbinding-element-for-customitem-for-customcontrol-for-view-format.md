---
title: Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065927"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="e2d29-102">Elemento ExpressionBinding para CustomItem for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="e2d29-103">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="e2d29-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e2d29-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2d29-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e2d29-105">Configuración (formato) elemento ViewDefinitions (formato) Vista (formato) del elemento control personalizado elemento de vista (formato) del elemento CustomEntries para el control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para el control personalizado para la vista ( Elemento de formato) CustomItem para CustomEntry para el control personalizado de vista (formato) del elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2d29-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e2d29-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e2d29-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e2d29-107">Attributes and Elements</span></span>

<span data-ttu-id="e2d29-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="e2d29-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2d29-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e2d29-109">Attributes</span></span>

<span data-ttu-id="e2d29-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e2d29-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2d29-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e2d29-111">Child Elements</span></span>

|<span data-ttu-id="e2d29-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e2d29-112">Element</span></span>|<span data-ttu-id="e2d29-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="e2d29-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e2d29-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e2d29-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e2d29-115">Define un control que se usa este control.</span><span class="sxs-lookup"><span data-stu-id="e2d29-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e2d29-116">Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e2d29-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e2d29-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e2d29-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="e2d29-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e2d29-119">Elemento EnumerateCollection para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e2d29-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e2d29-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e2d29-121">Especifica que se muestran los elementos de colecciones.</span><span class="sxs-lookup"><span data-stu-id="e2d29-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="e2d29-122">Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="e2d29-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e2d29-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e2d29-124">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="e2d29-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="e2d29-125">Elemento PropertyName para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e2d29-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e2d29-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e2d29-127">Especifica la propiedad de .NET cuyo valor se muestra el control.</span><span class="sxs-lookup"><span data-stu-id="e2d29-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="e2d29-128">Elemento de bloque de script para ExpressionBinding para CustomCustomControl para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e2d29-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e2d29-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e2d29-130">Especifica la secuencia de comandos cuyo valor se muestra el control.</span><span class="sxs-lookup"><span data-stu-id="e2d29-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2d29-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e2d29-131">Parent Elements</span></span>

|<span data-ttu-id="e2d29-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="e2d29-132">Element</span></span>|<span data-ttu-id="e2d29-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="e2d29-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2d29-134">Elemento CustomItem para CustomEntry para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="e2d29-135">Define qué datos se muestran la vista de control personalizado y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="e2d29-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2d29-136">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e2d29-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e2d29-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="e2d29-137">See Also</span></span>

[<span data-ttu-id="e2d29-138">Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2d29-139">Elemento EnumerateCollection para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2d29-140">Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="e2d29-141">Elemento PropertyName para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2d29-142">Elemento de bloque de script para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2d29-143">Elemento CustomItem para CustomEntry para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e2d29-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2d29-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2d29-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
