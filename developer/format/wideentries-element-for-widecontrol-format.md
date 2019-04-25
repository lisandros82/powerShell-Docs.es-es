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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083695"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="147fb-102">Elemento WideEntries para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="147fb-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="147fb-103">Proporciona las definiciones de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="147fb-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="147fb-104">La vista ampliada debe especificar una o varias definiciones.</span><span class="sxs-lookup"><span data-stu-id="147fb-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="147fb-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) WideEntries elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="147fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="147fb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="147fb-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="147fb-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="147fb-107">Attributes and Elements</span></span>

<span data-ttu-id="147fb-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `WideEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="147fb-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="147fb-109">Debe especificarse al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="147fb-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="147fb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="147fb-110">Attributes</span></span>

<span data-ttu-id="147fb-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="147fb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="147fb-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="147fb-112">Child Elements</span></span>

|<span data-ttu-id="147fb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="147fb-113">Element</span></span>|<span data-ttu-id="147fb-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="147fb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="147fb-115">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="147fb-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="147fb-116">Proporciona una definición de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="147fb-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="147fb-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="147fb-117">Parent Elements</span></span>

|<span data-ttu-id="147fb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="147fb-118">Element</span></span>|<span data-ttu-id="147fb-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="147fb-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="147fb-120">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="147fb-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="147fb-121">Define una amplia (valor single) formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="147fb-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="147fb-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="147fb-122">Remarks</span></span>

<span data-ttu-id="147fb-123">Una vista amplia es un formato de lista que muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="147fb-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="147fb-124">Para obtener más información acerca de los componentes de una vista amplia, consulte [los componentes de vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="147fb-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="147fb-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="147fb-125">Example</span></span>

<span data-ttu-id="147fb-126">El ejemplo siguiente se muestra un `WideEntries` elemento que define una sola `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="147fb-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="147fb-127">El `WideEntry` elemento contiene un único `WideItem` elemento que define qué valor de propiedad o el script se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="147fb-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="147fb-128">Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="147fb-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="147fb-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="147fb-129">See Also</span></span>

[<span data-ttu-id="147fb-130">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="147fb-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="147fb-131">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="147fb-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="147fb-132">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="147fb-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="147fb-133">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="147fb-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
