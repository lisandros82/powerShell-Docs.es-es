---
title: Elemento ExpressionBinding para CustomItem para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854931"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="88c97-102">Elemento ExpressionBinding para CustomItem for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="88c97-103">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="88c97-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="88c97-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="88c97-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="88c97-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para GroupBy (formato) (elemento) ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88c97-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="88c97-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="88c97-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="88c97-107">Attributes and Elements</span></span>

<span data-ttu-id="88c97-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="88c97-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88c97-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="88c97-109">Attributes</span></span>

<span data-ttu-id="88c97-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="88c97-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88c97-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="88c97-111">Child Elements</span></span>

|<span data-ttu-id="88c97-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="88c97-112">Element</span></span>|<span data-ttu-id="88c97-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="88c97-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="88c97-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="88c97-114">Optional element.</span></span><br /><br /> <span data-ttu-id="88c97-115">Define un control que se usa este control.</span><span class="sxs-lookup"><span data-stu-id="88c97-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="88c97-116">Elemento CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="88c97-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="88c97-117">Optional element.</span></span><br /><br /> <span data-ttu-id="88c97-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="88c97-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="88c97-119">[Elemento EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection (elemento) para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="88c97-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="88c97-120">Optional element.</span></span><br /><br /> <span data-ttu-id="88c97-121">Especifica que se muestran los elementos de colecciones.</span><span class="sxs-lookup"><span data-stu-id="88c97-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="88c97-122">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="88c97-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="88c97-123">Optional element.</span></span><br /><br /> <span data-ttu-id="88c97-124">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="88c97-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="88c97-125">Elemento PropertyName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="88c97-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="88c97-126">Optional element.</span></span><br /><br /> <span data-ttu-id="88c97-127">Especifica la propiedad de .NET cuyo valor se muestra el control.</span><span class="sxs-lookup"><span data-stu-id="88c97-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="88c97-128">Elemento de bloque de script para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="88c97-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="88c97-129">Optional element.</span></span><br /><br /> <span data-ttu-id="88c97-130">Especifica la secuencia de comandos cuyo valor se muestra el control.</span><span class="sxs-lookup"><span data-stu-id="88c97-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="88c97-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="88c97-131">Parent Elements</span></span>

|<span data-ttu-id="88c97-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="88c97-132">Element</span></span>|<span data-ttu-id="88c97-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="88c97-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88c97-134">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="88c97-135">Define qué datos se muestran la vista de control personalizado y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="88c97-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="88c97-136">Véase también</span><span class="sxs-lookup"><span data-stu-id="88c97-136">See Also</span></span>

[<span data-ttu-id="88c97-137">Elemento CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="88c97-138">Elemento EnumerateCollection para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="88c97-139">Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="88c97-140">Elemento PropertyName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="88c97-141">Elemento de bloque de script para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="88c97-142">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88c97-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="88c97-143">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="88c97-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
