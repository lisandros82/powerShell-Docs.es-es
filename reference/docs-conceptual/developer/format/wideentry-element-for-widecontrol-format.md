---
title: Elemento WideEntry para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367904"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="4eed9-102">Elemento WideEntry para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4eed9-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="4eed9-103">Proporciona una definición de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="4eed9-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="4eed9-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4eed9-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4eed9-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4eed9-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4eed9-106">Attributes and Elements</span></span>

<span data-ttu-id="4eed9-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideEntry`.</span><span class="sxs-lookup"><span data-stu-id="4eed9-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="4eed9-108">Debe especificar un único elemento secundario `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="4eed9-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4eed9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4eed9-109">Attributes</span></span>

<span data-ttu-id="4eed9-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4eed9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4eed9-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4eed9-111">Child Elements</span></span>

|<span data-ttu-id="4eed9-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4eed9-112">Element</span></span>|<span data-ttu-id="4eed9-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="4eed9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4eed9-114">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="4eed9-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4eed9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4eed9-116">Define los tipos .NET que usan esta definición de entrada ancha o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="4eed9-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="4eed9-117">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="4eed9-118">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="4eed9-118">Required element.</span></span><br /><br /> <span data-ttu-id="4eed9-119">Define la propiedad o el script cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="4eed9-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4eed9-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4eed9-120">Parent Elements</span></span>

|<span data-ttu-id="4eed9-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="4eed9-121">Element</span></span>|<span data-ttu-id="4eed9-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="4eed9-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4eed9-123">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="4eed9-124">Proporciona las definiciones de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="4eed9-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4eed9-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4eed9-125">Remarks</span></span>

<span data-ttu-id="4eed9-126">Una vista amplia es un formato de lista que muestra un valor de propiedad único o un valor de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="4eed9-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="4eed9-127">A diferencia de otros tipos de vistas, solo se puede especificar un elemento para cada definición de vista.</span><span class="sxs-lookup"><span data-stu-id="4eed9-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="4eed9-128">Para obtener más información sobre los demás componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4eed9-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4eed9-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4eed9-129">Example</span></span>

<span data-ttu-id="4eed9-130">En el ejemplo siguiente se muestra un elemento `WideEntry` que define un solo elemento `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="4eed9-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="4eed9-131">El elemento `WideItem` define la propiedad cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="4eed9-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="4eed9-132">Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="4eed9-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4eed9-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="4eed9-133">See Also</span></span>

[<span data-ttu-id="4eed9-134">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="4eed9-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4eed9-135">Elemento SelectionCondition para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4eed9-136">Elemento SelectionSetName para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4eed9-137">Elemento TypeName para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="4eed9-138">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="4eed9-139">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4eed9-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="4eed9-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eed9-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
