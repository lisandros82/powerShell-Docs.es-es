---
title: Elemento ListEntry para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362754"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="c942d-102">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c942d-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="c942d-103">Proporciona una definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="c942d-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="c942d-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c942d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c942d-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c942d-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="c942d-106">Attributes and Elements</span></span>

<span data-ttu-id="c942d-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListEntry`.</span><span class="sxs-lookup"><span data-stu-id="c942d-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c942d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c942d-108">Attributes</span></span>

<span data-ttu-id="c942d-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="c942d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c942d-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="c942d-110">Child Elements</span></span>

|<span data-ttu-id="c942d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="c942d-111">Element</span></span>|<span data-ttu-id="c942d-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="c942d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c942d-113">Elemento EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c942d-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c942d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c942d-115">Define los objetos .NET que usan esta definición de vista de lista o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="c942d-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c942d-116">ListItems (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c942d-117">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="c942d-117">Required element.</span></span><br /><br /> <span data-ttu-id="c942d-118">Define las propiedades y los scripts cuyos valores se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="c942d-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c942d-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="c942d-119">Parent Elements</span></span>

|<span data-ttu-id="c942d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c942d-120">Element</span></span>|<span data-ttu-id="c942d-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="c942d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c942d-122">ListEntries (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="c942d-123">Proporciona las definiciones de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="c942d-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c942d-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c942d-124">Remarks</span></span>

<span data-ttu-id="c942d-125">Una vista de lista es un formato de lista que muestra los valores de propiedad o los valores de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="c942d-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="c942d-126">Para obtener más información sobre las vistas de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c942d-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c942d-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c942d-127">Example</span></span>

<span data-ttu-id="c942d-128">En este ejemplo se muestran los elementos XML que definen la vista de lista para el objeto [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="c942d-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c942d-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="c942d-129">See Also</span></span>

[<span data-ttu-id="c942d-130">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="c942d-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c942d-131">Elemento EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c942d-132">ListEntries (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="c942d-133">ListItems (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="c942d-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c942d-134">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c942d-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
