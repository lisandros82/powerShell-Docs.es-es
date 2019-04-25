---
title: Elemento de bloque de script para ItemSelectionCondition de ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064414"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="cca8e-102">Elemento ScriptBlock para ItemSelectionCondition for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="cca8e-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="cca8e-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="cca8e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="cca8e-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa el elemento de lista.</span><span class="sxs-lookup"><span data-stu-id="cca8e-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="cca8e-105">Este elemento se usa al definir una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="cca8e-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="cca8e-106">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntries elemento ListItems de ListControl (formato) para ListEntry elemento ListItem de ListControl (formato) para ListItems de elemento de lista (formato) del Control ItemSelectionCondition para ListItem para elemento de bloque de script de ListControl (formato) de ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="cca8e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cca8e-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cca8e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cca8e-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="cca8e-108">Attributes and Elements</span></span>

<span data-ttu-id="cca8e-109">Las secciones siguientes describen los atributos, elementos secundarios y los elementos primarios de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="cca8e-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cca8e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cca8e-110">Attributes</span></span>

<span data-ttu-id="cca8e-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="cca8e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cca8e-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="cca8e-112">Child Elements</span></span>

<span data-ttu-id="cca8e-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="cca8e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cca8e-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="cca8e-114">Parent Elements</span></span>

|<span data-ttu-id="cca8e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="cca8e-115">Element</span></span>|<span data-ttu-id="cca8e-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="cca8e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cca8e-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="cca8e-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="cca8e-118">Define la condición que debe cumplirse para que este elemento de lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="cca8e-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cca8e-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="cca8e-119">Text Value</span></span>

<span data-ttu-id="cca8e-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="cca8e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="cca8e-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="cca8e-121">Remarks</span></span>

<span data-ttu-id="cca8e-122">Si se usa este elemento, no se puede especificar el `PropertyName` elemento cuando se define la condición de selección.</span><span class="sxs-lookup"><span data-stu-id="cca8e-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="cca8e-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="cca8e-123">See Also</span></span>

[<span data-ttu-id="cca8e-124">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cca8e-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
