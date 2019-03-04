---
title: Elemento PropertyName para ItemSelectionCondition de ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855541"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="b829c-102">Elemento PropertyName para ItemSelectionCondition for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b829c-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="b829c-103">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b829c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b829c-104">Cuando esta propiedad está presente o cuando se evalúa como `true`, se cumple la condición y se usa la vista.</span><span class="sxs-lookup"><span data-stu-id="b829c-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="b829c-105">Este elemento se usa al definir una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b829c-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="b829c-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) ListEntry elemento de configuración de elemento ListItems de ListControl (formato) para ListEntry para ListItem ListControl (formato) Elemento para ListItems de ListControl (formato) ItemSelectionCondition elemento para ListItem para el elemento PropertyName ListControls ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b829c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b829c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b829c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b829c-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b829c-108">Attributes and Elements</span></span>

<span data-ttu-id="b829c-109">Las secciones siguientes describen los atributos, elementos secundarios y los elementos primarios de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b829c-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b829c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b829c-110">Attributes</span></span>

<span data-ttu-id="b829c-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b829c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b829c-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b829c-112">Child Elements</span></span>

<span data-ttu-id="b829c-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b829c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b829c-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b829c-114">Parent Elements</span></span>

|<span data-ttu-id="b829c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b829c-115">Element</span></span>|<span data-ttu-id="b829c-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="b829c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b829c-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b829c-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="b829c-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b829c-118">Text Value</span></span>

<span data-ttu-id="b829c-119">Especifique el nombre de la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="b829c-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b829c-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b829c-120">Remarks</span></span>

<span data-ttu-id="b829c-121">Si se usa este elemento, no se puede especificar el [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="b829c-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b829c-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="b829c-122">See Also</span></span>

[<span data-ttu-id="b829c-123">Elemento de bloque de script para ItemSelectionCondition para ListIControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b829c-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="b829c-124">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b829c-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b829c-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b829c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
