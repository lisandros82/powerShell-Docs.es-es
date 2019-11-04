---
title: Elemento ExpressionBinding para CustomItem para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363194"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="26838-102">Elemento ExpressionBinding para CustomItem for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="26838-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="26838-103">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="26838-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="26838-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="26838-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="26838-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de Configuration ExpressionBinding Element for CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="26838-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26838-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="26838-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="26838-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="26838-107">Attributes and Elements</span></span>

<span data-ttu-id="26838-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="26838-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26838-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="26838-109">Attributes</span></span>

<span data-ttu-id="26838-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="26838-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26838-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="26838-111">Child Elements</span></span>

|<span data-ttu-id="26838-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="26838-112">Element</span></span>|<span data-ttu-id="26838-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="26838-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="26838-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="26838-114">Optional element.</span></span><br /><br /> <span data-ttu-id="26838-115">Define un control utilizado por este control.</span><span class="sxs-lookup"><span data-stu-id="26838-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="26838-116">Elemento CustomControlName de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="26838-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="26838-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="26838-117">Optional element.</span></span><br /><br /> <span data-ttu-id="26838-118">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="26838-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="26838-119">Elemento EnumerateCollection de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="26838-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="26838-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="26838-120">Optional element.</span></span><br /><br /> <span data-ttu-id="26838-121">Especifica que el control muestra los elementos de las colecciones.</span><span class="sxs-lookup"><span data-stu-id="26838-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="26838-122">Elemento ItemSelectionCondition de ExpressionBinding para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="26838-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="26838-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="26838-123">Optional element.</span></span><br /><br /> <span data-ttu-id="26838-124">Define la condición que debe existir para que se utilice este control común.</span><span class="sxs-lookup"><span data-stu-id="26838-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="26838-125">Elemento PropertyName para ExpressionBinding para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="26838-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="26838-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="26838-126">Optional element.</span></span><br /><br /> <span data-ttu-id="26838-127">Especifica la propiedad de .NET cuyo valor se muestra en el control común.</span><span class="sxs-lookup"><span data-stu-id="26838-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="26838-128">Elemento ScriptBlock para ExpressionBinding para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="26838-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="26838-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="26838-129">Optional element.</span></span><br /><br /> <span data-ttu-id="26838-130">Especifica el script cuyo valor muestra el control común.</span><span class="sxs-lookup"><span data-stu-id="26838-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="26838-131">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="26838-131">Parent Elements</span></span>

|<span data-ttu-id="26838-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="26838-132">Element</span></span>|<span data-ttu-id="26838-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="26838-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26838-134">Elemento CustomItem de CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="26838-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="26838-135">Define qué datos se muestran en la vista de control personalizada y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="26838-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="26838-136">Observaciones</span><span class="sxs-lookup"><span data-stu-id="26838-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="26838-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="26838-137">See Also</span></span>

[<span data-ttu-id="26838-138">Elemento CustomItem de CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="26838-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="26838-139">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="26838-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)