---
title: Elemento de bloque de script para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064516"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="bfbd4-102">Elemento ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfbd4-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="bfbd4-103">Especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="bfbd4-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de configuración (formato) de la vista de elemento de bloque de script para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfbd4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfbd4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bfbd4-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bfbd4-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="bfbd4-106">Attributes and Elements</span></span>

<span data-ttu-id="bfbd4-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfbd4-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="bfbd4-108">Attributes</span></span>

<span data-ttu-id="bfbd4-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfbd4-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="bfbd4-110">Child Elements</span></span>

<span data-ttu-id="bfbd4-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bfbd4-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="bfbd4-112">Parent Elements</span></span>

|<span data-ttu-id="bfbd4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="bfbd4-113">Element</span></span>|<span data-ttu-id="bfbd4-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="bfbd4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfbd4-115">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="bfbd4-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="bfbd4-116">Define cómo se muestra un grupo de objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bfbd4-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bfbd4-117">Text Value</span></span>

<span data-ttu-id="bfbd4-118">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfbd4-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bfbd4-119">Remarks</span></span>

<span data-ttu-id="bfbd4-120">Windows PowerShell se inicia un nuevo grupo cada vez que cambia el valor de esta secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="bfbd4-121">Cuando se especifica este elemento, no puede especificar el [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento para iniciar un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="bfbd4-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfbd4-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="bfbd4-122">See Also</span></span>

[<span data-ttu-id="bfbd4-123">Elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bfbd4-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="bfbd4-124">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="bfbd4-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="bfbd4-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfbd4-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
