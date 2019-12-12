---
title: Elemento WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367994"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="ed40f-102">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ed40f-102">WideControl Element (Format)</span></span>

<span data-ttu-id="ed40f-103">Define un formato de lista ancho (valor único) para la vista.</span><span class="sxs-lookup"><span data-stu-id="ed40f-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="ed40f-104">Esta vista muestra un valor de propiedad único o un valor de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="ed40f-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="ed40f-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed40f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ed40f-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed40f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ed40f-107">Attributes and Elements</span></span>

<span data-ttu-id="ed40f-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `WideControl`.</span><span class="sxs-lookup"><span data-stu-id="ed40f-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="ed40f-109">No se pueden especificar los elementos `AutoSize` y `ColumnNumber` al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="ed40f-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed40f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed40f-110">Attributes</span></span>

<span data-ttu-id="ed40f-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ed40f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed40f-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ed40f-112">Child Elements</span></span>

|<span data-ttu-id="ed40f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed40f-113">Element</span></span>|<span data-ttu-id="ed40f-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="ed40f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed40f-115">AutoSize (elemento) para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="ed40f-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ed40f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ed40f-117">Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="ed40f-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="ed40f-118">Elemento ColumnNumber para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="ed40f-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ed40f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ed40f-120">Especifica el número de columnas que se muestran en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="ed40f-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="ed40f-121">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="ed40f-122">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="ed40f-122">Required element.</span></span><br /><br /> <span data-ttu-id="ed40f-123">Proporciona las definiciones de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="ed40f-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ed40f-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ed40f-124">Parent Elements</span></span>

|<span data-ttu-id="ed40f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed40f-125">Element</span></span>|<span data-ttu-id="ed40f-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="ed40f-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed40f-127">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ed40f-128">Define una vista que se usa para mostrar uno o más objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="ed40f-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ed40f-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ed40f-129">Remarks</span></span>

<span data-ttu-id="ed40f-130">Al definir una vista ampliada, puede Agregar el elemento `AutoSize` o el `ColumnNumber`, pero no puede Agregar ambos.</span><span class="sxs-lookup"><span data-stu-id="ed40f-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="ed40f-131">En la mayoría de los casos, solo se requiere una definición para cada vista amplia, pero es posible tener varias definiciones si se desea usar la misma vista para mostrar diferentes objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="ed40f-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="ed40f-132">En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="ed40f-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="ed40f-133">Para obtener más información sobre los componentes de una vista amplia, vea [componentes de vista ancha](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ed40f-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ed40f-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ed40f-134">Example</span></span>

<span data-ttu-id="ed40f-135">En el ejemplo siguiente se muestra un elemento `WideControl` que se usa para mostrar una propiedad del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="ed40f-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="ed40f-136">Para obtener un ejemplo completo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="ed40f-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed40f-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="ed40f-137">See Also</span></span>

[<span data-ttu-id="ed40f-138">AutoSize (elemento) para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="ed40f-139">Elemento ColumnNumber para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="ed40f-140">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ed40f-141">Elemento WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="ed40f-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="ed40f-142">Vista amplia (básica)</span><span class="sxs-lookup"><span data-stu-id="ed40f-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="ed40f-143">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="ed40f-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ed40f-144">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed40f-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
