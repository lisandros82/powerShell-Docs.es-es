---
title: Elemento WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361404"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="2b474-102">Elemento WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2b474-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="2b474-103">Define la propiedad o el script cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="2b474-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="2b474-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry (Format) elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b474-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2b474-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b474-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2b474-106">Attributes and Elements</span></span>

<span data-ttu-id="2b474-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="2b474-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="2b474-108">El elemento `FormatString` es opcional.</span><span class="sxs-lookup"><span data-stu-id="2b474-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="2b474-109">Sin embargo, debe especificar un elemento `PropertyName` o `ScriptBlock`, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2b474-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b474-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2b474-110">Attributes</span></span>

<span data-ttu-id="2b474-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2b474-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b474-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2b474-112">Child Elements</span></span>

|<span data-ttu-id="2b474-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b474-113">Element</span></span>|<span data-ttu-id="2b474-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="2b474-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b474-115">Elemento FormatString para WideItem para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="2b474-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2b474-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2b474-117">Especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.</span><span class="sxs-lookup"><span data-stu-id="2b474-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="2b474-118">Elemento PropertyName para WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="2b474-119">Especifica la propiedad del objeto cuyo valor se muestra en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="2b474-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="2b474-120">Elemento ScriptBlock para WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="2b474-121">Especifica el script cuyo valor se muestra en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="2b474-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b474-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2b474-122">Parent Elements</span></span>

|<span data-ttu-id="2b474-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b474-123">Element</span></span>|<span data-ttu-id="2b474-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="2b474-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b474-125">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="2b474-126">Proporciona una definición de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="2b474-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b474-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2b474-127">Remarks</span></span>

<span data-ttu-id="2b474-128">Para obtener más información sobre los componentes de una vista amplia, vea [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2b474-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2b474-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2b474-129">Example</span></span>

<span data-ttu-id="2b474-130">En el ejemplo siguiente se muestra un elemento `WideEntry` que define un solo elemento `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="2b474-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="2b474-131">El elemento `WideItem` define la propiedad o el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="2b474-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="2b474-132">Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="2b474-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b474-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="2b474-133">See Also</span></span>

[<span data-ttu-id="2b474-134">Elemento FormatString para WideItem para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="2b474-135">Elemento PropertyName para WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="2b474-136">Elemento ScriptBlock para WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="2b474-137">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b474-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="2b474-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b474-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
