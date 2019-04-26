---
title: Ver elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083729"
---
# <a name="view-element-format"></a><span data-ttu-id="4680e-102">Elemento View (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-102">View Element (Format)</span></span>

<span data-ttu-id="4680e-103">Define una vista que muestra uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="4680e-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="4680e-104">No hay ningún límite al número de vistas que se pueden definir en un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="4680e-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="4680e-105">Elemento de vista de configuración (formato) del elemento elemento ViewDefinitions (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4680e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4680e-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="4680e-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4680e-107">Attributes and Elements</span></span>

<span data-ttu-id="4680e-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `View` elemento.</span><span class="sxs-lookup"><span data-stu-id="4680e-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="4680e-109">Debe especificar solo uno de los elementos secundarios de control, y debe especificar el nombre de la vista y los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="4680e-110">Definir controles personalizados, cómo agrupar objetos, y especifica si la vista está fuera de banda son opcionales.</span><span class="sxs-lookup"><span data-stu-id="4680e-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="4680e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4680e-111">Attributes</span></span>

<span data-ttu-id="4680e-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4680e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4680e-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4680e-113">Child Elements</span></span>

|<span data-ttu-id="4680e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="4680e-114">Element</span></span>|<span data-ttu-id="4680e-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="4680e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4680e-116">Los controles elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="4680e-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4680e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4680e-118">Define un conjunto de controles que pueden hacer referencia por su nombre desde dentro de la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="4680e-119">Elemento de control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4680e-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4680e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4680e-121">Define un formato de control personalizado para la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="4680e-122">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4680e-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4680e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="4680e-124">Define cómo se agrupan los miembros de los objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="4680e-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="4680e-125">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="4680e-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4680e-126">Optional element.</span></span><br /><br /> <span data-ttu-id="4680e-127">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="4680e-128">Elemento Name de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="4680e-129">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="4680e-129">Required element.</span></span><br /><br /> <span data-ttu-id="4680e-130">Especifica el nombre usado para hacer referencia a la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="4680e-131">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="4680e-132">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4680e-132">Optional element.</span></span><br /><br /> <span data-ttu-id="4680e-133">Define un formato de tabla para la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="4680e-134">Elemento ViewSelectedBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="4680e-135">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="4680e-135">Required element.</span></span><br /><br /> <span data-ttu-id="4680e-136">Define los objetos de .NET que muestra esta vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="4680e-137">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="4680e-138">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4680e-138">Optional element.</span></span><br /><br /> <span data-ttu-id="4680e-139">Define una amplia (valor single) formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="4680e-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4680e-140">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4680e-140">Parent Elements</span></span>

|<span data-ttu-id="4680e-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="4680e-141">Element</span></span>|<span data-ttu-id="4680e-142">Descripción</span><span class="sxs-lookup"><span data-stu-id="4680e-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4680e-143">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="4680e-144">Define las vistas que se usa para mostrar los objetos.</span><span class="sxs-lookup"><span data-stu-id="4680e-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4680e-145">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4680e-145">Remarks</span></span>

<span data-ttu-id="4680e-146">Para obtener más información acerca de los componentes de diferentes vistas y los controles personalizados, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="4680e-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="4680e-147">Componentes de vista de tabla</span><span class="sxs-lookup"><span data-stu-id="4680e-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="4680e-148">Componentes de vista de lista</span><span class="sxs-lookup"><span data-stu-id="4680e-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="4680e-149">Componentes de vista ampliada</span><span class="sxs-lookup"><span data-stu-id="4680e-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="4680e-150">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="4680e-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="4680e-151">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4680e-151">Example</span></span>

<span data-ttu-id="4680e-152">Este ejemplo se muestra un `View` elemento que define una vista de tabla para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="4680e-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4680e-153">Véase también</span><span class="sxs-lookup"><span data-stu-id="4680e-153">See Also</span></span>

[<span data-ttu-id="4680e-154">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="4680e-155">Elemento Name de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="4680e-156">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="4680e-157">Los controles elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="4680e-158">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4680e-159">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="4680e-160">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="4680e-161">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="4680e-162">Elemento de control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="4680e-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="4680e-163">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4680e-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
