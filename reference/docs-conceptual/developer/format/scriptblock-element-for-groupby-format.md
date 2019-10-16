---
title: Elemento ScriptBlock para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364934"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="7b53e-102">Elemento ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7b53e-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="7b53e-103">Especifica el script que inicia un nuevo grupo siempre que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="7b53e-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="7b53e-104">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento de elemento ScriptBlock de View (Format) para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b53e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b53e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7b53e-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b53e-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7b53e-106">Attributes and Elements</span></span>

<span data-ttu-id="7b53e-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="7b53e-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b53e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b53e-108">Attributes</span></span>

<span data-ttu-id="7b53e-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7b53e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b53e-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7b53e-110">Child Elements</span></span>

<span data-ttu-id="7b53e-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7b53e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b53e-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7b53e-112">Parent Elements</span></span>

|<span data-ttu-id="7b53e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b53e-113">Element</span></span>|<span data-ttu-id="7b53e-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="7b53e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b53e-115">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7b53e-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7b53e-116">Define cómo se muestra un grupo de objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="7b53e-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b53e-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7b53e-117">Text Value</span></span>

<span data-ttu-id="7b53e-118">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="7b53e-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b53e-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7b53e-119">Remarks</span></span>

<span data-ttu-id="7b53e-120">PowerShell inicia un nuevo grupo siempre que cambia el valor de este script.</span><span class="sxs-lookup"><span data-stu-id="7b53e-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="7b53e-121">Cuando se especifica este elemento, no se puede especificar el elemento [PropertyName](propertyname-element-for-groupby-format.md) para iniciar un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="7b53e-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b53e-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="7b53e-122">See Also</span></span>

[<span data-ttu-id="7b53e-123">Elemento PropertyName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b53e-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="7b53e-124">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7b53e-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="7b53e-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b53e-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
