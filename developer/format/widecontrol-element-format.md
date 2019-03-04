---
title: Elemento WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859831"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="d72c2-102">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-102">WideControl Element (Format)</span></span>

<span data-ttu-id="d72c2-103">Define una amplia (valor single) formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="d72c2-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="d72c2-104">Esta vista muestra un solo valor de propiedad o valor de la secuencia de comandos para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="d72c2-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="d72c2-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) WideControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d72c2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d72c2-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d72c2-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d72c2-107">Attributes and Elements</span></span>

<span data-ttu-id="d72c2-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `WideControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="d72c2-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="d72c2-109">No puede especificar el `AutoSize` y `ColumnNumber` elementos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="d72c2-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="d72c2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d72c2-110">Attributes</span></span>

<span data-ttu-id="d72c2-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d72c2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d72c2-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d72c2-112">Child Elements</span></span>

|<span data-ttu-id="d72c2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d72c2-113">Element</span></span>|<span data-ttu-id="d72c2-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="d72c2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d72c2-115">Elemento AutoSize para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="d72c2-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d72c2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d72c2-117">Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="d72c2-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="d72c2-118">Elemento ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="d72c2-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d72c2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d72c2-120">Especifica el número de columnas mostradas en la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="d72c2-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="d72c2-121">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="d72c2-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="d72c2-122">Required element.</span></span><br /><br /> <span data-ttu-id="d72c2-123">Proporciona las definiciones de la vista ampliada.</span><span class="sxs-lookup"><span data-stu-id="d72c2-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d72c2-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d72c2-124">Parent Elements</span></span>

|<span data-ttu-id="d72c2-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d72c2-125">Element</span></span>|<span data-ttu-id="d72c2-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="d72c2-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d72c2-127">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d72c2-128">Define una vista que se usa para mostrar uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="d72c2-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d72c2-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d72c2-129">Remarks</span></span>

<span data-ttu-id="d72c2-130">Al definir una vista amplia, puede agregar el `AutoSize` elemento o el `ColumnNumber` pero no se puede agregar ambos.</span><span class="sxs-lookup"><span data-stu-id="d72c2-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="d72c2-131">En la mayoría de los casos, solo una definición es necesaria para cada vista amplia, pero es posible tener varias definiciones si desea usar la misma vista para mostrar diferentes objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="d72c2-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d72c2-132">En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="d72c2-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="d72c2-133">Para obtener más información acerca de los componentes de una vista amplia, consulte [los componentes de vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d72c2-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d72c2-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d72c2-134">Example</span></span>

<span data-ttu-id="d72c2-135">El ejemplo siguiente se muestra un `WideControl` elemento que se usa para mostrar una propiedad de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="d72c2-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="d72c2-136">Para obtener un ejemplo completo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d72c2-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d72c2-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="d72c2-137">See Also</span></span>

[<span data-ttu-id="d72c2-138">Elemento AutoSize para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="d72c2-139">Elemento ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="d72c2-140">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d72c2-141">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="d72c2-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="d72c2-142">Vista amplia (Basic)</span><span class="sxs-lookup"><span data-stu-id="d72c2-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="d72c2-143">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="d72c2-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d72c2-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d72c2-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
