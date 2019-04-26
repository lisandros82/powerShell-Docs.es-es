---
title: Elemento ItemSelectionCondition para ExpressionBinding para el control personalizado (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065838"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="77eb0-102">Elemento ItemSelectionCondition para ExpressionBinding for CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="77eb0-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="77eb0-103">Define la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="77eb0-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="77eb0-104">No hay ningún límite al número de condiciones de selección que se pueden especificar para un elemento de control.</span><span class="sxs-lookup"><span data-stu-id="77eb0-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="77eb0-105">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="77eb0-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="77eb0-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry de vista (formato) del elemento ExpressionBinding para CustomItem para el control personalizado de vista (formato) ItemSelectionCondition del elemento de enlace de expresión para el control personalizado de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="77eb0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77eb0-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="77eb0-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77eb0-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="77eb0-108">Attributes and Elements</span></span>

<span data-ttu-id="77eb0-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="77eb0-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77eb0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="77eb0-110">Attributes</span></span>

<span data-ttu-id="77eb0-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="77eb0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77eb0-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="77eb0-112">Child Elements</span></span>

|<span data-ttu-id="77eb0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="77eb0-113">Element</span></span>|<span data-ttu-id="77eb0-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="77eb0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77eb0-115">Elemento PropertyName para ItemSelectionCondition para el control personalizado para (formato de vista</span><span class="sxs-lookup"><span data-stu-id="77eb0-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="77eb0-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="77eb0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="77eb0-117">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="77eb0-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="77eb0-118">Elemento de bloque de script para ItemSelectionCondition para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="77eb0-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="77eb0-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="77eb0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="77eb0-120">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="77eb0-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77eb0-121">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="77eb0-121">Parent Elements</span></span>

|<span data-ttu-id="77eb0-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="77eb0-122">Element</span></span>|<span data-ttu-id="77eb0-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="77eb0-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77eb0-124">Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="77eb0-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="77eb0-125">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="77eb0-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77eb0-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="77eb0-126">Remarks</span></span>

<span data-ttu-id="77eb0-127">Puede especificar un nombre de propiedad o un script para esta condición, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="77eb0-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="77eb0-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="77eb0-128">See Also</span></span>

[<span data-ttu-id="77eb0-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="77eb0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="77eb0-130">Elemento ExpressionBinding para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="77eb0-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
