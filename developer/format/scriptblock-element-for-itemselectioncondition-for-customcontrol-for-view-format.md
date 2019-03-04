---
title: Elemento de bloque de script para ItemSelectionCondition para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862241"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="544bc-102">Elemento ScriptBlock para ItemSelectionCondition for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="544bc-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="544bc-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="544bc-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="544bc-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el control.</span><span class="sxs-lookup"><span data-stu-id="544bc-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="544bc-105">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="544bc-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="544bc-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry de vista (formato) del elemento ExpressionBinding para CustomItem para el control personalizado de vista (formato) ItemSelectionCondition del elemento de enlace de expresión para el control personalizado de vista (formato) del elemento ScriptBlock para ItemSelectionCondition para Control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="544bc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="544bc-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="544bc-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="544bc-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="544bc-108">Attributes and Elements</span></span>

<span data-ttu-id="544bc-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="544bc-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="544bc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="544bc-110">Attributes</span></span>

<span data-ttu-id="544bc-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="544bc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="544bc-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="544bc-112">Child Elements</span></span>

<span data-ttu-id="544bc-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="544bc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="544bc-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="544bc-114">Parent Elements</span></span>

|<span data-ttu-id="544bc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="544bc-115">Element</span></span>|<span data-ttu-id="544bc-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="544bc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="544bc-117">Elemento ItemSelectionCondition para la expresión de enlace para el control personalizado de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="544bc-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="544bc-118">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="544bc-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="544bc-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="544bc-119">Text Value</span></span>

<span data-ttu-id="544bc-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="544bc-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="544bc-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="544bc-121">Remarks</span></span>

<span data-ttu-id="544bc-122">Si se usa este elemento, no se puede especificar el [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="544bc-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="544bc-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="544bc-123">See Also</span></span>

[<span data-ttu-id="544bc-124">Elemento PropertyName para ItemSelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="544bc-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="544bc-125">Elemento ItemSelectionCondition para la expresión de enlace para el control personalizado de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="544bc-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="544bc-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="544bc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
