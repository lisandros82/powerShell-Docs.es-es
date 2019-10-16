---
title: Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362104"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="bd311-102">Elemento ScriptBlock para ItemSelectionCondition for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="bd311-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="bd311-103">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="bd311-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bd311-104">Cuando este script se evalúa como `true`, se cumple la condición y se usa el elemento de lista.</span><span class="sxs-lookup"><span data-stu-id="bd311-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="bd311-105">Este elemento se utiliza al definir una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="bd311-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="bd311-106">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntries para ListControl (Format) elemento ListItems para ListEntry para ListControl (Format) elemento ListItem para ListItems para el elemento ItemSelectionCondition del control de lista (Format) para ListItem para ListControl (Format) elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bd311-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd311-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bd311-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd311-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="bd311-108">Attributes and Elements</span></span>

<span data-ttu-id="bd311-109">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="bd311-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd311-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd311-110">Attributes</span></span>

<span data-ttu-id="bd311-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bd311-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd311-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="bd311-112">Child Elements</span></span>

<span data-ttu-id="bd311-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bd311-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd311-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="bd311-114">Parent Elements</span></span>

|<span data-ttu-id="bd311-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd311-115">Element</span></span>|<span data-ttu-id="bd311-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="bd311-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd311-117">Elemento ItemSelectionCondition para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bd311-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bd311-118">Define la condición que debe existir para que se use este elemento de lista.</span><span class="sxs-lookup"><span data-stu-id="bd311-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd311-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bd311-119">Text Value</span></span>

<span data-ttu-id="bd311-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="bd311-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd311-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bd311-121">Remarks</span></span>

<span data-ttu-id="bd311-122">Si se usa este elemento, no se puede especificar el elemento `PropertyName` al definir la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="bd311-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd311-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="bd311-123">See Also</span></span>

[<span data-ttu-id="bd311-124">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd311-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
