---
title: Elemento ItemSelectionCondition para ExpressionBinding para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861851"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="00429-102">Elemento ItemSelectionCondition para ExpressionBinding for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="00429-103">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="00429-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="00429-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="00429-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="00429-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato) Elemento ItemSelectionCondition de ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00429-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="00429-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00429-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="00429-107">Attributes and Elements</span></span>

<span data-ttu-id="00429-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="00429-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00429-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="00429-109">Attributes</span></span>

<span data-ttu-id="00429-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="00429-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00429-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="00429-111">Child Elements</span></span>

|<span data-ttu-id="00429-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="00429-112">Element</span></span>|<span data-ttu-id="00429-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="00429-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00429-114">Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="00429-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="00429-115">Optional element.</span></span><br /><br /> <span data-ttu-id="00429-116">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="00429-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="00429-117">Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="00429-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="00429-118">Optional element.</span></span><br /><br /> <span data-ttu-id="00429-119">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="00429-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00429-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="00429-120">Parent Elements</span></span>

|<span data-ttu-id="00429-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="00429-121">Element</span></span>|<span data-ttu-id="00429-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="00429-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00429-123">Elemento ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="00429-124">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="00429-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00429-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="00429-125">Remarks</span></span>

<span data-ttu-id="00429-126">Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="00429-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="00429-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="00429-127">See Also</span></span>

[<span data-ttu-id="00429-128">Elemento PropertyName para ItemSelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="00429-129">Elemento de bloque de script para ItemSelectionCondition para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="00429-130">Elemento ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="00429-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="00429-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="00429-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
