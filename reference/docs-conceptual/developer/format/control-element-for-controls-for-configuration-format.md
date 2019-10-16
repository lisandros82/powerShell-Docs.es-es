---
title: Elemento control para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369014"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="e9af6-102">Elemento Control para Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="e9af6-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e9af6-103">Define un control común que pueden usar todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="e9af6-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="e9af6-104">Elemento Configuration (Format) elemento Controls de Configuration (Format) elemento control para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9af6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e9af6-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9af6-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e9af6-106">Attributes and Elements</span></span>

<span data-ttu-id="e9af6-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="e9af6-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="e9af6-108">Debe especificar solo uno de cada elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="e9af6-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9af6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e9af6-109">Attributes</span></span>

<span data-ttu-id="e9af6-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e9af6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9af6-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e9af6-111">Child Elements</span></span>

|<span data-ttu-id="e9af6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9af6-112">Element</span></span>|<span data-ttu-id="e9af6-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="e9af6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9af6-114">Elemento CustomControl para el control de los controles para la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="e9af6-115">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="e9af6-115">Required element.</span></span><br /><br /> <span data-ttu-id="e9af6-116">Define el control.</span><span class="sxs-lookup"><span data-stu-id="e9af6-116">Defines the control.</span></span>|
|[<span data-ttu-id="e9af6-117">Elemento Name del control para la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="e9af6-118">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="e9af6-118">Required element.</span></span><br /><br /> <span data-ttu-id="e9af6-119">Especifica el nombre usado para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="e9af6-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e9af6-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e9af6-120">Parent Elements</span></span>

|<span data-ttu-id="e9af6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9af6-121">Element</span></span>|<span data-ttu-id="e9af6-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="e9af6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9af6-123">Elemento Controls de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="e9af6-124">Define los controles comunes que se pueden usar en todas las vistas del archivo de formato o en otros controles.</span><span class="sxs-lookup"><span data-stu-id="e9af6-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e9af6-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e9af6-125">Remarks</span></span>

<span data-ttu-id="e9af6-126">Se puede hacer referencia al nombre dado a este control en los elementos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e9af6-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="e9af6-127">Elemento ExpressionBinding para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="e9af6-128">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="e9af6-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="e9af6-129">See Also</span></span>

[<span data-ttu-id="e9af6-130">Elemento Controls de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="e9af6-131">Elemento CustomControl para el control de la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e9af6-132">Elemento ExpressionBinding para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e9af6-133">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e9af6-134">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="e9af6-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e9af6-135">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9af6-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
