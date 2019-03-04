---
title: Elemento WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862631"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="f4ecc-102">Elemento WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="f4ecc-103">Define la propiedad o el script cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="f4ecc-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4ecc-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f4ecc-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4ecc-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f4ecc-106">Attributes and Elements</span></span>

<span data-ttu-id="f4ecc-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="f4ecc-108">El elemento `FormatString` es opcional.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="f4ecc-109">Sin embargo, debe especificar un `PropertyName` o `ScriptBlock` elemento, pero no se puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4ecc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ecc-110">Attributes</span></span>

<span data-ttu-id="f4ecc-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4ecc-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f4ecc-112">Child Elements</span></span>

|<span data-ttu-id="f4ecc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4ecc-113">Element</span></span>|<span data-ttu-id="f4ecc-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="f4ecc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4ecc-115">Elemento FormatString para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="f4ecc-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f4ecc-117">Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="f4ecc-118">Elemento PropertyName para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="f4ecc-119">Especifica la propiedad del objeto cuyo valor se muestra en la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="f4ecc-120">Elemento de bloque de script para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="f4ecc-121">Especifica la secuencia de comandos cuyo valor se muestra en la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f4ecc-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f4ecc-122">Parent Elements</span></span>

|<span data-ttu-id="f4ecc-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4ecc-123">Element</span></span>|<span data-ttu-id="f4ecc-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="f4ecc-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4ecc-125">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="f4ecc-126">Proporciona una definición de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4ecc-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f4ecc-127">Remarks</span></span>

<span data-ttu-id="f4ecc-128">Para obtener más información acerca de los componentes de una vista amplia, consulte [vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f4ecc-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f4ecc-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f4ecc-129">Example</span></span>

<span data-ttu-id="f4ecc-130">El ejemplo siguiente se muestra un `WideEntry` elemento que define una sola `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="f4ecc-131">El `WideItem` elemento define la propiedad o el script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="f4ecc-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="f4ecc-132">Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f4ecc-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4ecc-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="f4ecc-133">See Also</span></span>

[<span data-ttu-id="f4ecc-134">Elemento FormatString para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="f4ecc-135">Elemento PropertyName para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="f4ecc-136">Elemento de bloque de script para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="f4ecc-137">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f4ecc-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="f4ecc-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4ecc-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
