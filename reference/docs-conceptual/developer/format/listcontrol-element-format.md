---
title: ListControl (elemento, Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362784"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="88439-102">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="88439-102">ListControl Element (Format)</span></span>

<span data-ttu-id="88439-103">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="88439-103">Defines a list format for the view.</span></span>

<span data-ttu-id="88439-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="88439-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88439-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="88439-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="88439-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="88439-106">Attributes and Elements</span></span>

<span data-ttu-id="88439-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListControl`.</span><span class="sxs-lookup"><span data-stu-id="88439-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="88439-108">Este elemento debe contener un único elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="88439-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88439-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="88439-109">Attributes</span></span>

<span data-ttu-id="88439-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="88439-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88439-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="88439-111">Child Elements</span></span>

|<span data-ttu-id="88439-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="88439-112">Element</span></span>|<span data-ttu-id="88439-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="88439-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88439-114">ListEntries (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="88439-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="88439-115">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="88439-115">Required element.</span></span><br /><br /> <span data-ttu-id="88439-116">Proporciona las definiciones de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="88439-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="88439-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="88439-117">Parent Elements</span></span>

|<span data-ttu-id="88439-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="88439-118">Element</span></span>|<span data-ttu-id="88439-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="88439-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88439-120">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="88439-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="88439-121">Define una vista que se utiliza para mostrar los miembros de uno o más objetos.</span><span class="sxs-lookup"><span data-stu-id="88439-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="88439-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="88439-122">Remarks</span></span>

<span data-ttu-id="88439-123">Para obtener más información sobre cómo crear una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="88439-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="88439-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="88439-124">Example</span></span>

<span data-ttu-id="88439-125">En este ejemplo se muestra una vista de lista para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="88439-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="88439-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="88439-126">See Also</span></span>

[<span data-ttu-id="88439-127">Elemento View (Format)</span><span class="sxs-lookup"><span data-stu-id="88439-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="88439-128">ListEntries (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="88439-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="88439-129">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="88439-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="88439-130">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="88439-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)