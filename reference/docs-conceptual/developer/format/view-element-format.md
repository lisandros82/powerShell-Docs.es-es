---
title: Elemento View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361464"
---
# <a name="view-element-format"></a><span data-ttu-id="eccb5-102">Elemento View (formato)</span><span class="sxs-lookup"><span data-stu-id="eccb5-102">View Element (Format)</span></span>

<span data-ttu-id="eccb5-103">Define una vista que muestra uno o más objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="eccb5-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="eccb5-104">No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="eccb5-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="eccb5-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eccb5-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="eccb5-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eccb5-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="eccb5-107">Attributes and Elements</span></span>

<span data-ttu-id="eccb5-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `View`.</span><span class="sxs-lookup"><span data-stu-id="eccb5-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="eccb5-109">Debe especificar uno y solo uno de los elementos secundarios de control, y debe especificar el nombre de la vista y los objetos que la usan.</span><span class="sxs-lookup"><span data-stu-id="eccb5-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="eccb5-110">Definir controles personalizados, agrupar objetos y especificar si la vista está fuera de banda es opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="eccb5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="eccb5-111">Attributes</span></span>

<span data-ttu-id="eccb5-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="eccb5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eccb5-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="eccb5-113">Child Elements</span></span>

|<span data-ttu-id="eccb5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="eccb5-114">Element</span></span>|<span data-ttu-id="eccb5-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="eccb5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eccb5-116">Controls (elemento) para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="eccb5-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="eccb5-118">Define un conjunto de controles a los que se puede hacer referencia mediante su nombre desde dentro de la vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="eccb5-119">CustomControl (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="eccb5-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="eccb5-121">Define un formato de control personalizado para la vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="eccb5-122">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="eccb5-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="eccb5-124">Define cómo se agrupan los miembros de los objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="eccb5-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="eccb5-125">ListControl (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="eccb5-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-126">Optional element.</span></span><br /><br /> <span data-ttu-id="eccb5-127">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="eccb5-128">Name (elemento) para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="eccb5-129">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="eccb5-129">Required element.</span></span><br /><br /> <span data-ttu-id="eccb5-130">Especifica el nombre usado para hacer referencia a la vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="eccb5-131">Elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="eccb5-132">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-132">Optional element.</span></span><br /><br /> <span data-ttu-id="eccb5-133">Define un formato de tabla para la vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="eccb5-134">Elemento ViewSelectedBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="eccb5-135">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="eccb5-135">Required element.</span></span><br /><br /> <span data-ttu-id="eccb5-136">Define los objetos .NET que muestra esta vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="eccb5-137">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="eccb5-138">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eccb5-138">Optional element.</span></span><br /><br /> <span data-ttu-id="eccb5-139">Define un formato de lista ancho (valor único) para la vista.</span><span class="sxs-lookup"><span data-stu-id="eccb5-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eccb5-140">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="eccb5-140">Parent Elements</span></span>

|<span data-ttu-id="eccb5-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="eccb5-141">Element</span></span>|<span data-ttu-id="eccb5-142">Descripción</span><span class="sxs-lookup"><span data-stu-id="eccb5-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eccb5-143">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="eccb5-144">Define las vistas que se usan para mostrar los objetos.</span><span class="sxs-lookup"><span data-stu-id="eccb5-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eccb5-145">Observaciones</span><span class="sxs-lookup"><span data-stu-id="eccb5-145">Remarks</span></span>

<span data-ttu-id="eccb5-146">Para obtener más información sobre los componentes de diferentes vistas y controles personalizados, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="eccb5-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="eccb5-147">Componentes de vista de tabla</span><span class="sxs-lookup"><span data-stu-id="eccb5-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="eccb5-148">Componentes de la vista de lista</span><span class="sxs-lookup"><span data-stu-id="eccb5-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="eccb5-149">Componentes de vista ancha</span><span class="sxs-lookup"><span data-stu-id="eccb5-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="eccb5-150">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="eccb5-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="eccb5-151">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="eccb5-151">Example</span></span>

<span data-ttu-id="eccb5-152">En este ejemplo se muestra un elemento `View` que define una vista de tabla para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="eccb5-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="eccb5-153">Véase también</span><span class="sxs-lookup"><span data-stu-id="eccb5-153">See Also</span></span>

[<span data-ttu-id="eccb5-154">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="eccb5-155">Name (elemento) para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="eccb5-156">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="eccb5-157">Controls (elemento) para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="eccb5-158">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="eccb5-159">Elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="eccb5-160">ListControl (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="eccb5-161">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="eccb5-162">CustomControl (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="eccb5-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="eccb5-163">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eccb5-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
