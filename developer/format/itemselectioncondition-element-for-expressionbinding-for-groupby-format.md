---
title: Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065468"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="cc9f7-102">Elemento ItemSelectionCondition para ExpressionBinding for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc9f7-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="cc9f7-103">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="cc9f7-104">No hay ningún límite al número de condiciones de selección que se pueden especificar para un elemento de control.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="cc9f7-105">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cc9f7-106">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para GroupBy (formato) (elemento) ExpressionBinding para CustomItem para GroupBy (formato) (elemento) ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc9f7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc9f7-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cc9f7-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc9f7-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="cc9f7-108">Attributes and Elements</span></span>

<span data-ttu-id="cc9f7-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc9f7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc9f7-110">Attributes</span></span>

<span data-ttu-id="cc9f7-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc9f7-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="cc9f7-112">Child Elements</span></span>

|<span data-ttu-id="cc9f7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc9f7-113">Element</span></span>|<span data-ttu-id="cc9f7-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="cc9f7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc9f7-115">Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc9f7-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="cc9f7-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="cc9f7-117">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="cc9f7-118">Elemento de bloque de script para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc9f7-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="cc9f7-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="cc9f7-120">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc9f7-121">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="cc9f7-121">Parent Elements</span></span>

|<span data-ttu-id="cc9f7-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc9f7-122">Element</span></span>|<span data-ttu-id="cc9f7-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="cc9f7-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc9f7-124">Elemento ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc9f7-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="cc9f7-125">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc9f7-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="cc9f7-126">Remarks</span></span>

<span data-ttu-id="cc9f7-127">Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="cc9f7-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc9f7-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="cc9f7-128">See Also</span></span>

[<span data-ttu-id="cc9f7-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc9f7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="cc9f7-130">Elemento ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cc9f7-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
