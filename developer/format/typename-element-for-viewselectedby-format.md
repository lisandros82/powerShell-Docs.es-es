---
title: Elemento TypeName para ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083763"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="0c5c3-102">Elemento TypeName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0c5c3-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="0c5c3-103">Especifica un objeto .NET que se muestra la vista.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="0c5c3-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ViewSelectedBy (formato) TypeName elemento de configuración ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0c5c3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c5c3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0c5c3-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c5c3-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0c5c3-106">Attributes and Elements</span></span>

<span data-ttu-id="0c5c3-107">Las secciones siguientes describen los atributos, elementos secundarios y los elementos primarios de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c5c3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c5c3-108">Attributes</span></span>

<span data-ttu-id="0c5c3-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c5c3-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0c5c3-110">Child Elements</span></span>

<span data-ttu-id="0c5c3-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c5c3-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0c5c3-112">Parent Elements</span></span>

|<span data-ttu-id="0c5c3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c5c3-113">Element</span></span>|<span data-ttu-id="0c5c3-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c5c3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c5c3-115">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0c5c3-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="0c5c3-116">Define los objetos de .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c5c3-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="0c5c3-117">Text Value</span></span>

<span data-ttu-id="0c5c3-118">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c5c3-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0c5c3-119">Remarks</span></span>

<span data-ttu-id="0c5c3-120">Para obtener más información sobre cómo se usa este elemento en distintas vistas, consulte [crear una vista de tabla](./creating-a-table-view.md), [crear una vista de lista](./creating-a-list-view.md), [crear una vista amplia](./creating-a-wide-view.md), y [ Componentes de vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0c5c3-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c5c3-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c5c3-121">Example</span></span>

<span data-ttu-id="0c5c3-122">El ejemplo siguiente muestra cómo especificar el [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para obtener una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="0c5c3-123">Se usa el mismo esquema para las vistas de tabla, amplia y personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0c5c3-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0c5c3-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="0c5c3-124">See Also</span></span>

[<span data-ttu-id="0c5c3-125">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="0c5c3-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0c5c3-126">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="0c5c3-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0c5c3-127">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="0c5c3-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0c5c3-128">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="0c5c3-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0c5c3-129">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0c5c3-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="0c5c3-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c5c3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
