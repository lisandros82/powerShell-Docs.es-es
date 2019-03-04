---
title: Elemento ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857461"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="dd25f-102">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dd25f-102">ListControl Element (Format)</span></span>

<span data-ttu-id="dd25f-103">Define un formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="dd25f-103">Defines a list format for the view.</span></span>

<span data-ttu-id="dd25f-104">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="dd25f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd25f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dd25f-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd25f-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="dd25f-106">Attributes and Elements</span></span>

<span data-ttu-id="dd25f-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ListControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="dd25f-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="dd25f-108">Este elemento debe contener sólo un único elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="dd25f-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd25f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd25f-109">Attributes</span></span>

<span data-ttu-id="dd25f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="dd25f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd25f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="dd25f-111">Child Elements</span></span>

|<span data-ttu-id="dd25f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd25f-112">Element</span></span>|<span data-ttu-id="dd25f-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="dd25f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd25f-114">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="dd25f-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="dd25f-115">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="dd25f-115">Required element.</span></span><br /><br /> <span data-ttu-id="dd25f-116">Proporciona las definiciones de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="dd25f-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dd25f-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="dd25f-117">Parent Elements</span></span>

|<span data-ttu-id="dd25f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd25f-118">Element</span></span>|<span data-ttu-id="dd25f-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="dd25f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd25f-120">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="dd25f-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="dd25f-121">Define una vista que se usa para mostrar a los miembros de uno o varios objetos.</span><span class="sxs-lookup"><span data-stu-id="dd25f-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd25f-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="dd25f-122">Remarks</span></span>

<span data-ttu-id="dd25f-123">Para obtener más información acerca de cómo crear una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dd25f-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dd25f-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="dd25f-124">Example</span></span>

<span data-ttu-id="dd25f-125">En este ejemplo se muestra una vista de lista para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="dd25f-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd25f-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="dd25f-126">See Also</span></span>

[<span data-ttu-id="dd25f-127">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="dd25f-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="dd25f-128">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="dd25f-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="dd25f-129">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="dd25f-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dd25f-130">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="dd25f-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
