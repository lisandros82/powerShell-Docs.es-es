---
title: Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362914"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="b8f30-102">Elemento ItemSelectionCondition para ExpressionBinding for CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b8f30-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="b8f30-103">Define la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="b8f30-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b8f30-104">No hay ningún límite en el número de condiciones de selección que se pueden especificar para un elemento de control.</span><span class="sxs-lookup"><span data-stu-id="b8f30-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="b8f30-105">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="b8f30-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b8f30-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl para el elemento CustomEntry View (Format) para CustomEntries for View (Format) CustomItem para CustomEntry para View (Format) elemento ExpressionBinding para CustomItem para CustomControl para el elemento ItemSelectionCondition View (Format) para el enlace de expresiones para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8f30-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8f30-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b8f30-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8f30-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b8f30-108">Attributes and Elements</span></span>

<span data-ttu-id="b8f30-109">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="b8f30-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8f30-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8f30-110">Attributes</span></span>

<span data-ttu-id="b8f30-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b8f30-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8f30-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b8f30-112">Child Elements</span></span>

|<span data-ttu-id="b8f30-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8f30-113">Element</span></span>|<span data-ttu-id="b8f30-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="b8f30-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8f30-115">Elemento PropertyName para ItemSelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8f30-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="b8f30-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f30-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b8f30-117">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b8f30-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b8f30-118">Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8f30-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="b8f30-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f30-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b8f30-120">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b8f30-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8f30-121">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b8f30-121">Parent Elements</span></span>

|<span data-ttu-id="b8f30-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8f30-122">Element</span></span>|<span data-ttu-id="b8f30-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="b8f30-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8f30-124">Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8f30-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="b8f30-125">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="b8f30-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8f30-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b8f30-126">Remarks</span></span>

<span data-ttu-id="b8f30-127">Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b8f30-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8f30-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="b8f30-128">See Also</span></span>

[<span data-ttu-id="b8f30-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f30-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="b8f30-130">Elemento ExpressionBinding para CustomItem para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="b8f30-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
