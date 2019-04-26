---
title: Elemento ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083831"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="47647-102">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="47647-103">Define los objetos de .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="47647-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="47647-104">Cada vista debe especificar al menos un objeto. NET.</span><span class="sxs-lookup"><span data-stu-id="47647-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="47647-105">Elemento ViewDefinitions (formato) vista elemento (formato) ViewSelectedBy elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47647-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="47647-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47647-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="47647-107">Attributes and Elements</span></span>

<span data-ttu-id="47647-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ViewSelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="47647-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="47647-109">Este elemento debe contener al menos un `TypeName` o `SelectionSetName` elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="47647-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="47647-110">No hay ningún límite al número de elementos secundarios que se puede especificar ni su orden significativo.</span><span class="sxs-lookup"><span data-stu-id="47647-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="47647-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="47647-111">Attributes</span></span>

<span data-ttu-id="47647-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="47647-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47647-113">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="47647-113">Child Elements</span></span>

|<span data-ttu-id="47647-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="47647-114">Element</span></span>|<span data-ttu-id="47647-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="47647-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47647-116">Elemento TypeName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="47647-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="47647-117">Optional element.</span></span><br /><br /> <span data-ttu-id="47647-118">Especifica un objeto .NET que se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="47647-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="47647-119">Elemento SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="47647-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="47647-120">Optional element.</span></span><br /><br /> <span data-ttu-id="47647-121">Especifica un conjunto de objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="47647-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47647-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="47647-122">Parent Elements</span></span>

|<span data-ttu-id="47647-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="47647-123">Element</span></span>|<span data-ttu-id="47647-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="47647-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47647-125">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="47647-126">Define una vista que muestra uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="47647-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47647-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="47647-127">Remarks</span></span>

<span data-ttu-id="47647-128">Para obtener más información sobre cómo se usa este elemento en distintas vistas, consulte [los componentes de vista de tabla](./creating-a-table-view.md), [los componentes de vista de lista](./creating-a-list-view.md), [los componentes de vista amplia](./creating-a-wide-view.md)y [Control personalizado componentes](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="47647-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="47647-129">El `SelectionSetName` elemento se usa cuando el archivo de formato define un conjunto de objetos que se muestran en varias vistas.</span><span class="sxs-lookup"><span data-stu-id="47647-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="47647-130">Para obtener más información acerca de cómo se definen y se hace referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="47647-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="47647-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="47647-131">Example</span></span>

<span data-ttu-id="47647-132">El ejemplo siguiente muestra cómo especificar el [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para obtener una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="47647-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="47647-133">Se usa el mismo esquema para las vistas de tabla, amplia y personalizadas.</span><span class="sxs-lookup"><span data-stu-id="47647-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="47647-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="47647-134">See Also</span></span>

[<span data-ttu-id="47647-135">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="47647-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="47647-136">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="47647-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="47647-137">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="47647-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="47647-138">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="47647-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="47647-139">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="47647-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="47647-140">Elemento SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="47647-141">Elemento TypeName (formato)</span><span class="sxs-lookup"><span data-stu-id="47647-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="47647-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="47647-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
