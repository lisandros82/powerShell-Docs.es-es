---
title: Elemento WideEntries para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361434"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="cf899-102">Elemento WideEntries para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="cf899-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="cf899-103">Proporciona las definiciones de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="cf899-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="cf899-104">La vista ancha debe especificar una o más definiciones.</span><span class="sxs-lookup"><span data-stu-id="cf899-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="cf899-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="cf899-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf899-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cf899-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf899-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="cf899-107">Attributes and Elements</span></span>

<span data-ttu-id="cf899-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideEntries`.</span><span class="sxs-lookup"><span data-stu-id="cf899-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="cf899-109">Se debe especificar al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="cf899-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf899-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cf899-110">Attributes</span></span>

<span data-ttu-id="cf899-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="cf899-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf899-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="cf899-112">Child Elements</span></span>

|<span data-ttu-id="cf899-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf899-113">Element</span></span>|<span data-ttu-id="cf899-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="cf899-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf899-115">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cf899-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="cf899-116">Proporciona una definición de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="cf899-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cf899-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="cf899-117">Parent Elements</span></span>

|<span data-ttu-id="cf899-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="cf899-118">Element</span></span>|<span data-ttu-id="cf899-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="cf899-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf899-120">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cf899-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="cf899-121">Define un formato de lista ancho (valor único) para la vista.</span><span class="sxs-lookup"><span data-stu-id="cf899-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cf899-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="cf899-122">Remarks</span></span>

<span data-ttu-id="cf899-123">Una vista amplia es un formato de lista que muestra un valor de propiedad único o un valor de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="cf899-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="cf899-124">Para obtener más información sobre los componentes de una vista amplia, vea [componentes de vista ancha](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cf899-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf899-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="cf899-125">Example</span></span>

<span data-ttu-id="cf899-126">En el ejemplo siguiente se muestra un elemento `WideEntries` que define un solo elemento `WideEntry`.</span><span class="sxs-lookup"><span data-stu-id="cf899-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="cf899-127">El elemento `WideEntry` contiene un solo elemento `WideItem` que define qué propiedad o valor de script se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="cf899-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="cf899-128">Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="cf899-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf899-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="cf899-129">See Also</span></span>

[<span data-ttu-id="cf899-130">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="cf899-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cf899-131">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cf899-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="cf899-132">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cf899-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="cf899-133">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf899-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
