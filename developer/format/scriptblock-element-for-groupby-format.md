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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856211"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="d6c90-102">Elemento ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c90-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="d6c90-103">Especifica la secuencia de comandos que se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="d6c90-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="d6c90-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de configuración (formato) de la vista de elemento de bloque de script para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c90-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6c90-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d6c90-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6c90-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d6c90-106">Attributes and Elements</span></span>

<span data-ttu-id="d6c90-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="d6c90-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6c90-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6c90-108">Attributes</span></span>

<span data-ttu-id="d6c90-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d6c90-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6c90-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d6c90-110">Child Elements</span></span>

<span data-ttu-id="d6c90-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d6c90-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d6c90-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d6c90-112">Parent Elements</span></span>

|<span data-ttu-id="d6c90-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6c90-113">Element</span></span>|<span data-ttu-id="d6c90-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="d6c90-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6c90-115">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c90-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="d6c90-116">Define cómo se muestra un grupo de objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="d6c90-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d6c90-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d6c90-117">Text Value</span></span>

<span data-ttu-id="d6c90-118">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="d6c90-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c90-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d6c90-119">Remarks</span></span>

<span data-ttu-id="d6c90-120">Windows PowerShell se inicia un nuevo grupo cada vez que cambia el valor de esta secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="d6c90-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="d6c90-121">Cuando se especifica este elemento, no puede especificar el [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento para iniciar un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="d6c90-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c90-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="d6c90-122">See Also</span></span>

[<span data-ttu-id="d6c90-123">Elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c90-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="d6c90-124">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="d6c90-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d6c90-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6c90-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
