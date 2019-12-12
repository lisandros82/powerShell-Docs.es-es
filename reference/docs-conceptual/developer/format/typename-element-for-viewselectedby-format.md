---
title: Elemento TypeName para ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361444"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="e1969-102">Elemento TypeName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e1969-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="e1969-103">Especifica un objeto .NET que se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="e1969-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="e1969-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento TypeName para ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e1969-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1969-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e1969-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1969-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e1969-106">Attributes and Elements</span></span>

<span data-ttu-id="e1969-107">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="e1969-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1969-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1969-108">Attributes</span></span>

<span data-ttu-id="e1969-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1969-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1969-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e1969-110">Child Elements</span></span>

<span data-ttu-id="e1969-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1969-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1969-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e1969-112">Parent Elements</span></span>

|<span data-ttu-id="e1969-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1969-113">Element</span></span>|<span data-ttu-id="e1969-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="e1969-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1969-115">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e1969-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="e1969-116">Define los objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="e1969-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1969-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e1969-117">Text Value</span></span>

<span data-ttu-id="e1969-118">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="e1969-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1969-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e1969-119">Remarks</span></span>

<span data-ttu-id="e1969-120">Para obtener más información sobre cómo se usa este elemento en diferentes vistas, vea [crear una vista de tabla](./creating-a-table-view.md), [crear una vista de lista](./creating-a-list-view.md), [crear una vista amplia](./creating-a-wide-view.md)y [componentes de vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e1969-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1969-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e1969-121">Example</span></span>

<span data-ttu-id="e1969-122">En el ejemplo siguiente se muestra cómo especificar el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) para una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e1969-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="e1969-123">Se usa el mismo esquema para las vistas de tabla, ancho y personalizado.</span><span class="sxs-lookup"><span data-stu-id="e1969-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="e1969-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="e1969-124">See Also</span></span>

[<span data-ttu-id="e1969-125">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="e1969-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e1969-126">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="e1969-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e1969-127">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="e1969-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e1969-128">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="e1969-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e1969-129">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e1969-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="e1969-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1969-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
