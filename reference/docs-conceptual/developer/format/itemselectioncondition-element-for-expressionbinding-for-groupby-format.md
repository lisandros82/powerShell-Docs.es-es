---
title: Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365294"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="e0216-102">Elemento ItemSelectionCondition para ExpressionBinding for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e0216-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="e0216-103">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="e0216-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e0216-104">No hay ningún límite en el número de condiciones de selección que se pueden especificar para un elemento de control.</span><span class="sxs-lookup"><span data-stu-id="e0216-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="e0216-105">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="e0216-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e0216-106">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) ItemSelectionCondition para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0216-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0216-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e0216-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0216-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e0216-108">Attributes and Elements</span></span>

<span data-ttu-id="e0216-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="e0216-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0216-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0216-110">Attributes</span></span>

<span data-ttu-id="e0216-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e0216-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0216-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e0216-112">Child Elements</span></span>

|<span data-ttu-id="e0216-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0216-113">Element</span></span>|<span data-ttu-id="e0216-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="e0216-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0216-115">Elemento PropertyName para ItemSelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0216-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="e0216-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e0216-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e0216-117">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e0216-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e0216-118">Elemento ScriptBlock para ItemSelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0216-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="e0216-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e0216-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e0216-120">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e0216-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0216-121">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e0216-121">Parent Elements</span></span>

|<span data-ttu-id="e0216-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0216-122">Element</span></span>|<span data-ttu-id="e0216-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="e0216-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0216-124">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0216-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e0216-125">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="e0216-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0216-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e0216-126">Remarks</span></span>

<span data-ttu-id="e0216-127">Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="e0216-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0216-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="e0216-128">See Also</span></span>

[<span data-ttu-id="e0216-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0216-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="e0216-130">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0216-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
