---
title: Elemento PropertyName para ItemSelectionCondition para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064873"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e5022-102">Elemento PropertyName para ItemSelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="e5022-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e5022-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e5022-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e5022-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="e5022-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e5022-105">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="e5022-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e5022-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry de vista (formato) del elemento ExpressionBinding para CustomItem para el control personalizado de vista (formato) ItemSelectionCondition del elemento de enlace de expresión para el control personalizado de vista (formato) del elemento PropertyName para ItemSelectionCondition para Control personalizado para (formato de vista</span><span class="sxs-lookup"><span data-stu-id="e5022-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="e5022-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e5022-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5022-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e5022-108">Attributes and Elements</span></span>

<span data-ttu-id="e5022-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e5022-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5022-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e5022-110">Attributes</span></span>

<span data-ttu-id="e5022-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e5022-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5022-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e5022-112">Child Elements</span></span>

<span data-ttu-id="e5022-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e5022-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5022-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e5022-114">Parent Elements</span></span>

|<span data-ttu-id="e5022-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5022-115">Element</span></span>|<span data-ttu-id="e5022-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="e5022-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5022-117">Elemento ItemSelectionCondition para la expresión de enlace para el control personalizado de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e5022-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="e5022-118">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="e5022-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5022-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e5022-119">Text Value</span></span>

<span data-ttu-id="e5022-120">Especifique el nombre de la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="e5022-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5022-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e5022-121">Remarks</span></span>

<span data-ttu-id="e5022-122">Si se usa este elemento, no se puede especificar el [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="e5022-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5022-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="e5022-123">See Also</span></span>

[<span data-ttu-id="e5022-124">Elemento de bloque de script para ItemSelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e5022-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5022-125">Elemento ItemSelectionCondition para la expresión de enlace para el control personalizado de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="e5022-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="e5022-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5022-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
