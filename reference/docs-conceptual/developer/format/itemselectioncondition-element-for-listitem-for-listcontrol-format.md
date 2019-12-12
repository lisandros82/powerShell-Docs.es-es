---
title: Elemento ItemSelectionCondition para ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365194"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="1eda6-102">Elemento ItemSelectionCondition para ListItem for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1eda6-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="1eda6-103">Define la condición que debe existir para que se use este elemento de lista.</span><span class="sxs-lookup"><span data-stu-id="1eda6-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="1eda6-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntries para ListControl (Format) elemento ListItems para ListEntry para ListControl (Format) elemento ListItem para ListItems para ListControl (Format) elemento ItemSelectionCondition para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1eda6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1eda6-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1eda6-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1eda6-106">Attributes and Elements</span></span>

<span data-ttu-id="1eda6-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="1eda6-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1eda6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="1eda6-108">Attributes</span></span>

<span data-ttu-id="1eda6-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1eda6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1eda6-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1eda6-110">Child Elements</span></span>

|<span data-ttu-id="1eda6-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="1eda6-111">Element</span></span>|<span data-ttu-id="1eda6-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="1eda6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1eda6-113">Elemento PropertyName para ItemSelectionCondition para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="1eda6-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1eda6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1eda6-115">Especifica la propiedad de .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="1eda6-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1eda6-116">Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="1eda6-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1eda6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1eda6-118">Especifica el script que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="1eda6-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1eda6-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1eda6-119">Parent Elements</span></span>

|<span data-ttu-id="1eda6-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1eda6-120">Element</span></span>|<span data-ttu-id="1eda6-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="1eda6-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1eda6-122">Elemento ListItem para ListItems para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="1eda6-123">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1eda6-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1eda6-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1eda6-124">Remarks</span></span>

<span data-ttu-id="1eda6-125">Puede especificar un nombre de propiedad o un script para esta condición, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1eda6-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1eda6-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="1eda6-126">See Also</span></span>

[<span data-ttu-id="1eda6-127">Elemento ListItem para ListItems para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="1eda6-128">Elemento PropertyName para ItemSelectionCondition para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="1eda6-129">Elemento ScriptBlock para ItemSelectionCondition para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1eda6-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="1eda6-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1eda6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
