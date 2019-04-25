---
title: Elemento ListEntries para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065400"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="7c27f-102">Elemento ListEntries para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7c27f-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="7c27f-103">Proporciona las definiciones de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7c27f-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="7c27f-104">La vista de lista debe especificar una o varias definiciones.</span><span class="sxs-lookup"><span data-stu-id="7c27f-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="7c27f-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="7c27f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c27f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7c27f-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c27f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7c27f-107">Attributes and Elements</span></span>

<span data-ttu-id="7c27f-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ListEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="7c27f-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="7c27f-109">Debe especificarse al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="7c27f-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c27f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c27f-110">Attributes</span></span>

<span data-ttu-id="7c27f-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7c27f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c27f-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7c27f-112">Child Elements</span></span>

|<span data-ttu-id="7c27f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c27f-113">Element</span></span>|<span data-ttu-id="7c27f-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="7c27f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c27f-115">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7c27f-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="7c27f-116">Proporciona una definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7c27f-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c27f-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7c27f-117">Parent Elements</span></span>

|<span data-ttu-id="7c27f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c27f-118">Element</span></span>|<span data-ttu-id="7c27f-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="7c27f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c27f-120">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7c27f-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="7c27f-121">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="7c27f-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c27f-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7c27f-122">Remarks</span></span>

<span data-ttu-id="7c27f-123">Para obtener más información acerca de las vistas de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7c27f-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c27f-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7c27f-124">Example</span></span>

<span data-ttu-id="7c27f-125">En este ejemplo se muestra los elementos XML que definen la vista de lista para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="7c27f-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7c27f-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="7c27f-126">See Also</span></span>

[<span data-ttu-id="7c27f-127">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7c27f-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="7c27f-128">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7c27f-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="7c27f-129">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="7c27f-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7c27f-130">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="7c27f-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
