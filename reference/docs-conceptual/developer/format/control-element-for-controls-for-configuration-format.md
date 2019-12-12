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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369014"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="456cc-102">Elemento Control para Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="456cc-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="456cc-103">Define un control común que pueden usar todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="456cc-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="456cc-104">Elemento Configuration (Format) elemento Controls de Configuration (Format) elemento control para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="456cc-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="456cc-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="456cc-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="456cc-106">Attributes and Elements</span></span>

<span data-ttu-id="456cc-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="456cc-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="456cc-108">Debe especificar solo uno de cada elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="456cc-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="456cc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="456cc-109">Attributes</span></span>

<span data-ttu-id="456cc-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="456cc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="456cc-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="456cc-111">Child Elements</span></span>

|<span data-ttu-id="456cc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="456cc-112">Element</span></span>|<span data-ttu-id="456cc-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="456cc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="456cc-114">Elemento CustomControl para el control de los controles para la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="456cc-115">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="456cc-115">Required element.</span></span><br /><br /> <span data-ttu-id="456cc-116">Define el control.</span><span class="sxs-lookup"><span data-stu-id="456cc-116">Defines the control.</span></span>|
|[<span data-ttu-id="456cc-117">Elemento Name del control para la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="456cc-118">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="456cc-118">Required element.</span></span><br /><br /> <span data-ttu-id="456cc-119">Especifica el nombre usado para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="456cc-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="456cc-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="456cc-120">Parent Elements</span></span>

|<span data-ttu-id="456cc-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="456cc-121">Element</span></span>|<span data-ttu-id="456cc-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="456cc-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="456cc-123">Elemento Controls de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="456cc-124">Define los controles comunes que se pueden usar en todas las vistas del archivo de formato o en otros controles.</span><span class="sxs-lookup"><span data-stu-id="456cc-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="456cc-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="456cc-125">Remarks</span></span>

<span data-ttu-id="456cc-126">Se puede hacer referencia al nombre dado a este control en los elementos siguientes:</span><span class="sxs-lookup"><span data-stu-id="456cc-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="456cc-127">Elemento ExpressionBinding para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="456cc-128">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="456cc-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="456cc-129">See Also</span></span>

[<span data-ttu-id="456cc-130">Elemento Controls de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="456cc-131">Elemento CustomControl para el control de la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="456cc-132">Elemento ExpressionBinding para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="456cc-133">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="456cc-134">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="456cc-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="456cc-135">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="456cc-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
