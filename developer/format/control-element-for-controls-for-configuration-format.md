---
title: Elemento de control para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858891"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="109e2-102">Elemento Control para Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="109e2-103">Define un control común que puede usarse en todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="109e2-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="109e2-104">Elemento de configuración elemento (formato de) los controles de elemento de Control de configuración (formato) para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="109e2-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="109e2-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="109e2-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="109e2-106">Attributes and Elements</span></span>

<span data-ttu-id="109e2-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario para el `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="109e2-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="109e2-108">Debe especificar solo uno de cada elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="109e2-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="109e2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="109e2-109">Attributes</span></span>

<span data-ttu-id="109e2-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="109e2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="109e2-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="109e2-111">Child Elements</span></span>

|<span data-ttu-id="109e2-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="109e2-112">Element</span></span>|<span data-ttu-id="109e2-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="109e2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="109e2-114">Elemento de control personalizado para el Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="109e2-115">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="109e2-115">Required element.</span></span><br /><br /> <span data-ttu-id="109e2-116">Define el control.</span><span class="sxs-lookup"><span data-stu-id="109e2-116">Defines the control.</span></span>|
|[<span data-ttu-id="109e2-117">Elemento Name de Control para la configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="109e2-118">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="109e2-118">Required element.</span></span><br /><br /> <span data-ttu-id="109e2-119">Especifica el nombre usado para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="109e2-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="109e2-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="109e2-120">Parent Elements</span></span>

|<span data-ttu-id="109e2-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="109e2-121">Element</span></span>|<span data-ttu-id="109e2-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="109e2-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="109e2-123">Los controles elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="109e2-124">Define los controles comunes que pueden usarse por todas las vistas del archivo de formato o por otros controles.</span><span class="sxs-lookup"><span data-stu-id="109e2-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="109e2-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="109e2-125">Remarks</span></span>

<span data-ttu-id="109e2-126">El nombre asignado a este control puede hacer referencia a los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="109e2-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="109e2-127">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="109e2-128">Elemento GroupBy para View(Format)</span><span class="sxs-lookup"><span data-stu-id="109e2-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="109e2-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="109e2-129">See Also</span></span>

[<span data-ttu-id="109e2-130">Los controles elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="109e2-131">Elemento de control personalizado para el Control de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="109e2-132">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="109e2-133">Elemento GroupBy para View(Format)</span><span class="sxs-lookup"><span data-stu-id="109e2-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="109e2-134">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="109e2-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="109e2-135">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="109e2-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
