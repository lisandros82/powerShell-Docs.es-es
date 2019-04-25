---
title: Elemento ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065230"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="13001-102">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="13001-103">Proporciona una definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="13001-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="13001-104">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) ListEntry elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13001-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="13001-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13001-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="13001-106">Attributes and Elements</span></span>

<span data-ttu-id="13001-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ListEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="13001-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13001-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="13001-108">Attributes</span></span>

<span data-ttu-id="13001-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="13001-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13001-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="13001-110">Child Elements</span></span>

|<span data-ttu-id="13001-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="13001-111">Element</span></span>|<span data-ttu-id="13001-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="13001-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13001-113">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="13001-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="13001-114">Optional element.</span></span><br /><br /> <span data-ttu-id="13001-115">Define los objetos de .NET que usan esta definición de vista de lista o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="13001-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="13001-116">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="13001-117">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="13001-117">Required element.</span></span><br /><br /> <span data-ttu-id="13001-118">Define las propiedades y las secuencias de comandos cuyos valores se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="13001-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13001-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="13001-119">Parent Elements</span></span>

|<span data-ttu-id="13001-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="13001-120">Element</span></span>|<span data-ttu-id="13001-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="13001-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13001-122">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="13001-123">Proporciona las definiciones de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="13001-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13001-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="13001-124">Remarks</span></span>

<span data-ttu-id="13001-125">Una vista de lista es un formato de lista que muestra los valores de propiedad o valores de secuencia de comandos para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="13001-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="13001-126">Para obtener más información acerca de las vistas de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="13001-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="13001-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="13001-127">Example</span></span>

<span data-ttu-id="13001-128">En este ejemplo se muestra los elementos XML que definen la vista de lista para la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="13001-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="13001-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="13001-129">See Also</span></span>

[<span data-ttu-id="13001-130">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="13001-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="13001-131">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="13001-132">Elemento ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="13001-133">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="13001-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="13001-134">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="13001-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
