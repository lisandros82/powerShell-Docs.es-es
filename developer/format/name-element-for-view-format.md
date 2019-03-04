---
title: Nombre de elemento de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859511"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="8d1b2-102">Elemento Name para View (formato)</span><span class="sxs-lookup"><span data-stu-id="8d1b2-102">Name Element for View (Format)</span></span>

<span data-ttu-id="8d1b2-103">Especifica el nombre que se usa para identificar la vista.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="8d1b2-104">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) nombre elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="8d1b2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8d1b2-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8d1b2-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8d1b2-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8d1b2-106">Attributes and Elements</span></span>

<span data-ttu-id="8d1b2-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="8d1b2-108">Solo un `Name` se admite el elemento para cada vista.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="8d1b2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d1b2-109">Attributes</span></span>

<span data-ttu-id="8d1b2-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8d1b2-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8d1b2-111">Child Elements</span></span>

<span data-ttu-id="8d1b2-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8d1b2-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8d1b2-113">Parent Elements</span></span>

|<span data-ttu-id="8d1b2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d1b2-114">Element</span></span>|<span data-ttu-id="8d1b2-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d1b2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8d1b2-116">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8d1b2-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="8d1b2-117">Define una vista que se usa para mostrar a los miembros de uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8d1b2-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8d1b2-118">Text Value</span></span>

<span data-ttu-id="8d1b2-119">Especifique un nombre descriptivo único para la vista.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="8d1b2-120">Este nombre puede incluir una referencia al tipo de la vista (por ejemplo, una vista de tabla o vista de lista), qué objeto o conjunto de objetos de utilizar la vista, ¿qué comando devuelve los objetos o una combinación de estos.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d1b2-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8d1b2-121">Remarks</span></span>

<span data-ttu-id="8d1b2-122">Para obtener más información sobre los diferentes tipos de vistas, vea los temas siguientes: [Vista de tabla](./creating-a-table-view.md), [vista de lista](./creating-a-list-view.md), [vista amplia](./creating-a-wide-view.md), y [vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8d1b2-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="8d1b2-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8d1b2-123">Example</span></span>

<span data-ttu-id="8d1b2-124">El ejemplo siguiente se muestra un `View` elemento que define una vista de tabla para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="8d1b2-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="8d1b2-125">El nombre de la vista es "servicio".</span><span class="sxs-lookup"><span data-stu-id="8d1b2-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="8d1b2-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="8d1b2-126">See Also</span></span>

[<span data-ttu-id="8d1b2-127">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="8d1b2-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8d1b2-128">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="8d1b2-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8d1b2-129">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="8d1b2-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8d1b2-130">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="8d1b2-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8d1b2-131">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8d1b2-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="8d1b2-132">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d1b2-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
