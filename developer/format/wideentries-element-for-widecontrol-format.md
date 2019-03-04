---
title: Elemento WideEntries para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853281"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="9d3ac-102">Elemento WideEntries para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9d3ac-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="9d3ac-103">Proporciona las definiciones de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="9d3ac-104">La vista ampliada debe especificar una o varias definiciones.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="9d3ac-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) WideEntries elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="9d3ac-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d3ac-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9d3ac-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d3ac-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9d3ac-107">Attributes and Elements</span></span>

<span data-ttu-id="9d3ac-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `WideEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="9d3ac-109">Debe especificarse al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d3ac-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d3ac-110">Attributes</span></span>

<span data-ttu-id="9d3ac-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d3ac-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9d3ac-112">Child Elements</span></span>

|<span data-ttu-id="9d3ac-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d3ac-113">Element</span></span>|<span data-ttu-id="9d3ac-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="9d3ac-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d3ac-115">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d3ac-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="9d3ac-116">Proporciona una definición de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9d3ac-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9d3ac-117">Parent Elements</span></span>

|<span data-ttu-id="9d3ac-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d3ac-118">Element</span></span>|<span data-ttu-id="9d3ac-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="9d3ac-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d3ac-120">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9d3ac-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="9d3ac-121">Define una amplia (valor single) formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9d3ac-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9d3ac-122">Remarks</span></span>

<span data-ttu-id="9d3ac-123">Una vista amplia es un formato de lista que muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="9d3ac-124">Para obtener más información acerca de los componentes de una vista amplia, consulte [los componentes de vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9d3ac-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9d3ac-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9d3ac-125">Example</span></span>

<span data-ttu-id="9d3ac-126">El ejemplo siguiente se muestra un `WideEntries` elemento que define una sola `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="9d3ac-127">El `WideEntry` elemento contiene un único `WideItem` elemento que define qué valor de propiedad o el script se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="9d3ac-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="9d3ac-128">Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="9d3ac-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d3ac-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="9d3ac-129">See Also</span></span>

[<span data-ttu-id="9d3ac-130">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="9d3ac-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9d3ac-131">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9d3ac-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="9d3ac-132">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d3ac-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="9d3ac-133">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d3ac-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
