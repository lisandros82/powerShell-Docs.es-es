---
title: Elemento ListEntries para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362764"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="ad726-102">Elemento ListEntries para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ad726-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="ad726-103">Proporciona las definiciones de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="ad726-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="ad726-104">La vista de lista debe especificar una o más definiciones.</span><span class="sxs-lookup"><span data-stu-id="ad726-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="ad726-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="ad726-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad726-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ad726-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad726-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ad726-107">Attributes and Elements</span></span>

<span data-ttu-id="ad726-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListEntries`.</span><span class="sxs-lookup"><span data-stu-id="ad726-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="ad726-109">Se debe especificar al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="ad726-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad726-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ad726-110">Attributes</span></span>

<span data-ttu-id="ad726-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ad726-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad726-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ad726-112">Child Elements</span></span>

|<span data-ttu-id="ad726-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ad726-113">Element</span></span>|<span data-ttu-id="ad726-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="ad726-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad726-115">ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ad726-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="ad726-116">Proporciona una definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="ad726-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ad726-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ad726-117">Parent Elements</span></span>

|<span data-ttu-id="ad726-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ad726-118">Element</span></span>|<span data-ttu-id="ad726-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="ad726-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad726-120">ListControl (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="ad726-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="ad726-121">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="ad726-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad726-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ad726-122">Remarks</span></span>

<span data-ttu-id="ad726-123">Para obtener más información sobre las vistas de lista, vea [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ad726-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ad726-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ad726-124">Example</span></span>

<span data-ttu-id="ad726-125">En este ejemplo se muestran los elementos XML que definen la vista de lista para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="ad726-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad726-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="ad726-126">See Also</span></span>

[<span data-ttu-id="ad726-127">ListControl (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="ad726-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="ad726-128">ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ad726-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="ad726-129">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="ad726-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ad726-130">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad726-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
