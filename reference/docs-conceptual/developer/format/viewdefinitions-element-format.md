---
title: Elemento ViewDefinitions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361424"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="f74d8-102">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="f74d8-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="f74d8-103">Define las vistas que se usan para mostrar objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="f74d8-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="f74d8-104">Estas vistas pueden mostrar las propiedades y los valores de script de un objeto en formato de tabla, formato de lista, formato ancho y formato de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="f74d8-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="f74d8-105">Elemento Configuration (Format) ViewDefinitions (Format XML) (elemento)</span><span class="sxs-lookup"><span data-stu-id="f74d8-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="f74d8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f74d8-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f74d8-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f74d8-107">Attributes and Elements</span></span>

<span data-ttu-id="f74d8-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ViewDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="f74d8-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="f74d8-109">No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato y se pueden agregar en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="f74d8-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="f74d8-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f74d8-110">Attributes</span></span>

<span data-ttu-id="f74d8-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f74d8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f74d8-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f74d8-112">Child Elements</span></span>

|<span data-ttu-id="f74d8-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f74d8-113">Element</span></span>|<span data-ttu-id="f74d8-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="f74d8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f74d8-115">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="f74d8-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="f74d8-116">Define una vista que se usa para mostrar uno o más objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="f74d8-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f74d8-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f74d8-117">Parent Elements</span></span>

|<span data-ttu-id="f74d8-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="f74d8-118">Element</span></span>|<span data-ttu-id="f74d8-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="f74d8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f74d8-120">Configuration (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="f74d8-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="f74d8-121">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f74d8-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f74d8-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f74d8-122">Remarks</span></span>

<span data-ttu-id="f74d8-123">Para obtener más información acerca de los componentes de los diferentes tipos de vistas, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="f74d8-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="f74d8-124">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="f74d8-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="f74d8-125">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="f74d8-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="f74d8-126">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="f74d8-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="f74d8-127">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="f74d8-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="f74d8-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f74d8-128">Example</span></span>

<span data-ttu-id="f74d8-129">En este ejemplo se muestra un elemento `ViewDefinitions` que contiene los elementos primarios de una vista de tabla y una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f74d8-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="f74d8-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="f74d8-130">See Also</span></span>

[<span data-ttu-id="f74d8-131">Configuration (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="f74d8-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="f74d8-132">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="f74d8-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="f74d8-133">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="f74d8-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f74d8-134">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="f74d8-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f74d8-135">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="f74d8-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f74d8-136">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="f74d8-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="f74d8-137">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f74d8-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
