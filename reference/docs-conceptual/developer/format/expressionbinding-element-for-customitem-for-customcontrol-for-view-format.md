---
title: Elemento ExpressionBinding para CustomItem para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363154"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="012c9-102">Elemento ExpressionBinding para CustomItem for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="012c9-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="012c9-103">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="012c9-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="012c9-104">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="012c9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="012c9-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento CustomEntries de la vista (Format) para CustomControl para la vista (Format) CustomEntry para CustomEntries para CustomControl para View ( Format) elemento CustomItem para CustomEntry para CustomControl para la vista (Format) elemento ExpressionBinding para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="012c9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="012c9-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="012c9-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="012c9-107">Attributes and Elements</span></span>

<span data-ttu-id="012c9-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="012c9-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="012c9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="012c9-109">Attributes</span></span>

<span data-ttu-id="012c9-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="012c9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="012c9-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="012c9-111">Child Elements</span></span>

|<span data-ttu-id="012c9-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="012c9-112">Element</span></span>|<span data-ttu-id="012c9-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="012c9-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="012c9-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="012c9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="012c9-115">Define un control utilizado por este control.</span><span class="sxs-lookup"><span data-stu-id="012c9-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="012c9-116">Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="012c9-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="012c9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="012c9-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="012c9-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="012c9-119">Elemento EnumerateCollection para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="012c9-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="012c9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="012c9-121">Especifica que se muestran los elementos de las colecciones.</span><span class="sxs-lookup"><span data-stu-id="012c9-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="012c9-122">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="012c9-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="012c9-123">Optional element.</span></span><br /><br /> <span data-ttu-id="012c9-124">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="012c9-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="012c9-125">Elemento PropertyName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="012c9-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="012c9-126">Optional element.</span></span><br /><br /> <span data-ttu-id="012c9-127">Especifica la propiedad de .NET cuyo valor muestra el control.</span><span class="sxs-lookup"><span data-stu-id="012c9-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="012c9-128">Elemento ScriptBlock para ExpressionBinding para CustomCustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="012c9-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="012c9-129">Optional element.</span></span><br /><br /> <span data-ttu-id="012c9-130">Especifica el script cuyo valor muestra el control.</span><span class="sxs-lookup"><span data-stu-id="012c9-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="012c9-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="012c9-131">Parent Elements</span></span>

|<span data-ttu-id="012c9-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="012c9-132">Element</span></span>|<span data-ttu-id="012c9-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="012c9-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="012c9-134">Elemento CustomItem para CustomEntry para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="012c9-135">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="012c9-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="012c9-136">Observaciones</span><span class="sxs-lookup"><span data-stu-id="012c9-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="012c9-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="012c9-137">See Also</span></span>

[<span data-ttu-id="012c9-138">Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="012c9-139">Elemento EnumerateCollection para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="012c9-140">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="012c9-141">Elemento PropertyName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="012c9-142">Elemento ScriptBlock para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="012c9-143">Elemento CustomItem para CustomEntry para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="012c9-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="012c9-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="012c9-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
