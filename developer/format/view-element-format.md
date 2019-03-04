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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856151"
---
# <a name="view-element-format"></a><span data-ttu-id="9e6b1-102">Elemento View (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-102">View Element (Format)</span></span>

<span data-ttu-id="9e6b1-103">Define una vista que muestra uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="9e6b1-104">No hay ningún límite al número de vistas que se pueden definir en un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="9e6b1-105">Elemento de vista de configuración (formato) del elemento elemento ViewDefinitions (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e6b1-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9e6b1-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9e6b1-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9e6b1-107">Attributes and Elements</span></span>

<span data-ttu-id="9e6b1-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `View` elemento.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="9e6b1-109">Debe especificar solo uno de los elementos secundarios de control, y debe especificar el nombre de la vista y los objetos que utilizan la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="9e6b1-110">Definir controles personalizados, cómo agrupar objetos, y especifica si la vista está fuera de banda son opcionales.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e6b1-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9e6b1-111">Attributes</span></span>

<span data-ttu-id="9e6b1-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e6b1-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9e6b1-113">Child Elements</span></span>

|<span data-ttu-id="9e6b1-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e6b1-114">Element</span></span>|<span data-ttu-id="9e6b1-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="9e6b1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e6b1-116">Los controles elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="9e6b1-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9e6b1-118">Define un conjunto de controles que pueden hacer referencia por su nombre desde dentro de la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="9e6b1-119">Elemento de control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="9e6b1-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9e6b1-121">Define un formato de control personalizado para la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="9e6b1-122">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="9e6b1-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9e6b1-124">Define cómo se agrupan los miembros de los objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="9e6b1-125">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="9e6b1-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9e6b1-127">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="9e6b1-128">Elemento Name de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="9e6b1-129">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-129">Required element.</span></span><br /><br /> <span data-ttu-id="9e6b1-130">Especifica el nombre usado para hacer referencia a la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="9e6b1-131">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="9e6b1-132">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-132">Optional element.</span></span><br /><br /> <span data-ttu-id="9e6b1-133">Define un formato de tabla para la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="9e6b1-134">Elemento ViewSelectedBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="9e6b1-135">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-135">Required element.</span></span><br /><br /> <span data-ttu-id="9e6b1-136">Define los objetos de .NET que muestra esta vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="9e6b1-137">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="9e6b1-138">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-138">Optional element.</span></span><br /><br /> <span data-ttu-id="9e6b1-139">Define una amplia (valor single) formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9e6b1-140">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9e6b1-140">Parent Elements</span></span>

|<span data-ttu-id="9e6b1-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e6b1-141">Element</span></span>|<span data-ttu-id="9e6b1-142">Descripción</span><span class="sxs-lookup"><span data-stu-id="9e6b1-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e6b1-143">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="9e6b1-144">Define las vistas que se usa para mostrar los objetos.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e6b1-145">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9e6b1-145">Remarks</span></span>

<span data-ttu-id="9e6b1-146">Para obtener más información acerca de los componentes de diferentes vistas y los controles personalizados, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="9e6b1-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="9e6b1-147">Componentes de vista de tabla</span><span class="sxs-lookup"><span data-stu-id="9e6b1-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="9e6b1-148">Componentes de vista de lista</span><span class="sxs-lookup"><span data-stu-id="9e6b1-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="9e6b1-149">Componentes de vista ampliada</span><span class="sxs-lookup"><span data-stu-id="9e6b1-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="9e6b1-150">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="9e6b1-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="9e6b1-151">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9e6b1-151">Example</span></span>

<span data-ttu-id="9e6b1-152">Este ejemplo se muestra un `View` elemento que define una vista de tabla para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="9e6b1-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e6b1-153">Véase también</span><span class="sxs-lookup"><span data-stu-id="9e6b1-153">See Also</span></span>

[<span data-ttu-id="9e6b1-154">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="9e6b1-155">Elemento Name de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="9e6b1-156">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="9e6b1-157">Los controles elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="9e6b1-158">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9e6b1-159">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="9e6b1-160">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="9e6b1-161">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="9e6b1-162">Elemento de control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="9e6b1-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="9e6b1-163">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e6b1-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
