---
title: Elemento Label para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365204"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="7dd42-102">Elemento Label para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7dd42-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="7dd42-103">Especifica una etiqueta que se muestra cuando se encuentra un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="7dd42-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="7dd42-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy para el elemento Label (Format) para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd42-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7dd42-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7dd42-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7dd42-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7dd42-106">Attributes and Elements</span></span>

<span data-ttu-id="7dd42-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Label`.</span><span class="sxs-lookup"><span data-stu-id="7dd42-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7dd42-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="7dd42-108">Attributes</span></span>

<span data-ttu-id="7dd42-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7dd42-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7dd42-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7dd42-110">Child Elements</span></span>

<span data-ttu-id="7dd42-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7dd42-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7dd42-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7dd42-112">Parent Elements</span></span>

|<span data-ttu-id="7dd42-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7dd42-113">Element</span></span>|<span data-ttu-id="7dd42-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="7dd42-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7dd42-115">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd42-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7dd42-116">Define cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="7dd42-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7dd42-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7dd42-117">Text Value</span></span>

<span data-ttu-id="7dd42-118">Especifique el texto que se muestra cuando Windows PowerShell encuentra un nuevo valor de propiedad o script.</span><span class="sxs-lookup"><span data-stu-id="7dd42-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="7dd42-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7dd42-119">Remarks</span></span>

<span data-ttu-id="7dd42-120">Además del texto especificado por este elemento, Windows PowerShell muestra el nuevo valor que inicia el grupo y agrega una línea en blanco antes y después del grupo.</span><span class="sxs-lookup"><span data-stu-id="7dd42-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="7dd42-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7dd42-121">Example</span></span>

<span data-ttu-id="7dd42-122">En el ejemplo siguiente se muestra la etiqueta de un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="7dd42-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="7dd42-123">La etiqueta mostrada tendría un aspecto similar al siguiente: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="7dd42-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="7dd42-124">Para obtener un ejemplo de un archivo de formato completo que incluye este elemento, vea [vista ancha (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="7dd42-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd42-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="7dd42-125">See Also</span></span>

[<span data-ttu-id="7dd42-126">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd42-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7dd42-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd42-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
