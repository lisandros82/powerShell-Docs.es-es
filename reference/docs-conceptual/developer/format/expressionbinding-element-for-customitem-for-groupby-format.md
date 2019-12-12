---
title: Elemento ExpressionBinding para CustomItem para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368634"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="9a76f-102">Elemento ExpressionBinding para CustomItem for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9a76f-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="9a76f-103">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="9a76f-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="9a76f-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="9a76f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9a76f-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para GroupBy (Format) elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a76f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9a76f-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9a76f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9a76f-107">Attributes and Elements</span></span>

<span data-ttu-id="9a76f-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="9a76f-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a76f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a76f-109">Attributes</span></span>

<span data-ttu-id="9a76f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a76f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a76f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9a76f-111">Child Elements</span></span>

|<span data-ttu-id="9a76f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a76f-112">Element</span></span>|<span data-ttu-id="9a76f-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="9a76f-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="9a76f-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9a76f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9a76f-115">Define un control utilizado por este control.</span><span class="sxs-lookup"><span data-stu-id="9a76f-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="9a76f-116">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9a76f-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9a76f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9a76f-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="9a76f-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="9a76f-119">[Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="9a76f-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9a76f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9a76f-121">Especifica que se muestran los elementos de las colecciones.</span><span class="sxs-lookup"><span data-stu-id="9a76f-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="9a76f-122">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9a76f-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9a76f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9a76f-124">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="9a76f-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="9a76f-125">Elemento PropertyName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9a76f-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9a76f-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9a76f-127">Especifica la propiedad de .NET cuyo valor muestra el control.</span><span class="sxs-lookup"><span data-stu-id="9a76f-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="9a76f-128">Elemento ScriptBlock para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9a76f-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9a76f-129">Optional element.</span></span><br /><br /> <span data-ttu-id="9a76f-130">Especifica el script cuyo valor muestra el control.</span><span class="sxs-lookup"><span data-stu-id="9a76f-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9a76f-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9a76f-131">Parent Elements</span></span>

|<span data-ttu-id="9a76f-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a76f-132">Element</span></span>|<span data-ttu-id="9a76f-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="9a76f-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a76f-134">Elemento CustomItem para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9a76f-135">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="9a76f-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9a76f-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="9a76f-136">See Also</span></span>

[<span data-ttu-id="9a76f-137">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9a76f-138">Elemento EnumerateCollection para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9a76f-139">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9a76f-140">Elemento PropertyName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9a76f-141">Elemento ScriptBlock para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9a76f-142">Elemento CustomItem para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a76f-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9a76f-143">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a76f-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
