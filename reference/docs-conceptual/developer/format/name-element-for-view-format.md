---
title: Name (elemento) para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362644"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="8101d-102">Elemento Name para View (formato)</span><span class="sxs-lookup"><span data-stu-id="8101d-102">Name Element for View (Format)</span></span>

<span data-ttu-id="8101d-103">Especifica el nombre que se utiliza para identificar la vista.</span><span class="sxs-lookup"><span data-stu-id="8101d-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="8101d-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Name (Format)</span><span class="sxs-lookup"><span data-stu-id="8101d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8101d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8101d-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8101d-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8101d-106">Attributes and Elements</span></span>

<span data-ttu-id="8101d-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="8101d-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="8101d-108">Solo se permite un elemento `Name` para cada vista.</span><span class="sxs-lookup"><span data-stu-id="8101d-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="8101d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8101d-109">Attributes</span></span>

<span data-ttu-id="8101d-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8101d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8101d-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8101d-111">Child Elements</span></span>

<span data-ttu-id="8101d-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8101d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8101d-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8101d-113">Parent Elements</span></span>

|<span data-ttu-id="8101d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8101d-114">Element</span></span>|<span data-ttu-id="8101d-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8101d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8101d-116">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="8101d-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="8101d-117">Define una vista que se usa para mostrar los miembros de uno o más objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="8101d-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8101d-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8101d-118">Text Value</span></span>

<span data-ttu-id="8101d-119">Especifique un nombre descriptivo único para la vista.</span><span class="sxs-lookup"><span data-stu-id="8101d-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="8101d-120">Este nombre puede incluir una referencia al tipo de la vista (por ejemplo, una vista de tabla o una vista de lista), qué objeto o conjunto de objetos usan la vista, qué comando devuelve los objetos o una combinación de ellos.</span><span class="sxs-lookup"><span data-stu-id="8101d-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="8101d-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8101d-121">Remarks</span></span>

<span data-ttu-id="8101d-122">Para obtener más información sobre los diferentes tipos de vistas, vea los temas siguientes [: vista de tabla](./creating-a-table-view.md), vista de [lista](./creating-a-list-view.md), [vista ampliada](./creating-a-wide-view.md)y [vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8101d-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="8101d-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8101d-123">Example</span></span>

<span data-ttu-id="8101d-124">En el ejemplo siguiente se muestra un elemento `View` que define una vista de tabla para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="8101d-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="8101d-125">El nombre de la vista es "Service".</span><span class="sxs-lookup"><span data-stu-id="8101d-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="8101d-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="8101d-126">See Also</span></span>

[<span data-ttu-id="8101d-127">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="8101d-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8101d-128">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="8101d-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8101d-129">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="8101d-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8101d-130">Crear controles personalizados</span><span class="sxs-lookup"><span data-stu-id="8101d-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8101d-131">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="8101d-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="8101d-132">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8101d-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
