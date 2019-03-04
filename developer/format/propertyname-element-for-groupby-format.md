---
title: Elemento PropertyName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863271"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="5fd14-102">Elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5fd14-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="5fd14-103">Especifica la propiedad de .NET que se inicia un nuevo grupo cada vez que cambia su valor.</span><span class="sxs-lookup"><span data-stu-id="5fd14-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="5fd14-104">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de vista (formato) del elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5fd14-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5fd14-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5fd14-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fd14-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="5fd14-106">Attributes and Elements</span></span>

<span data-ttu-id="5fd14-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="5fd14-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fd14-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5fd14-108">Attributes</span></span>

<span data-ttu-id="5fd14-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5fd14-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5fd14-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="5fd14-110">Child Elements</span></span>

<span data-ttu-id="5fd14-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5fd14-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5fd14-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="5fd14-112">Parent Elements</span></span>

|<span data-ttu-id="5fd14-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5fd14-113">Element</span></span>|<span data-ttu-id="5fd14-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="5fd14-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5fd14-115">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="5fd14-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="5fd14-116">Define cómo se muestra un grupo de objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="5fd14-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5fd14-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5fd14-117">Text Value</span></span>

<span data-ttu-id="5fd14-118">Especifique el nombre de propiedad. NET.</span><span class="sxs-lookup"><span data-stu-id="5fd14-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fd14-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5fd14-119">Remarks</span></span>

<span data-ttu-id="5fd14-120">Windows PowerShell se inicia un nuevo grupo cada vez que cambia el valor de esta propiedad.</span><span class="sxs-lookup"><span data-stu-id="5fd14-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="5fd14-121">Cuando se especifica este elemento, no puede especificar el [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento para iniciar un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="5fd14-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="5fd14-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5fd14-122">Example</span></span>

<span data-ttu-id="5fd14-123">El ejemplo siguiente muestra cómo iniciar un nuevo grupo cuando cambia el valor de una propiedad.</span><span class="sxs-lookup"><span data-stu-id="5fd14-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="5fd14-124">Para obtener un ejemplo de un archivo de formato completo que incluye este elemento, vea [vista amplia (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="5fd14-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fd14-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="5fd14-125">See Also</span></span>

[<span data-ttu-id="5fd14-126">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="5fd14-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5fd14-127">Elemento de bloque de script para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5fd14-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="5fd14-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fd14-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
