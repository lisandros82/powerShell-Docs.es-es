---
title: Elemento ListItems para ListEntry para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362744"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="e1748-102">Elemento ListItems para ListEntry for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e1748-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="e1748-103">Define las propiedades y los scripts cuyos valores se muestran en las filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e1748-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="e1748-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para el elemento de lista (Format) elemento ListEntry para ListControl (Format) elemento ListItems para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e1748-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1748-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e1748-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1748-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e1748-106">Attributes and Elements</span></span>

<span data-ttu-id="e1748-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListItems`.</span><span class="sxs-lookup"><span data-stu-id="e1748-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="e1748-108">No hay ningún límite en el número de elementos secundarios que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="e1748-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="e1748-109">El orden de los elementos secundarios define el orden en que se muestran los valores en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e1748-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1748-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1748-110">Attributes</span></span>

<span data-ttu-id="e1748-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1748-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1748-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e1748-112">Child Elements</span></span>

|<span data-ttu-id="e1748-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1748-113">Element</span></span>|<span data-ttu-id="e1748-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="e1748-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1748-115">Elemento ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e1748-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e1748-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="e1748-116">Required element.</span></span><br /><br /> <span data-ttu-id="e1748-117">Define la propiedad o el script cuyo valor se muestra en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e1748-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1748-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e1748-118">Parent Elements</span></span>

|<span data-ttu-id="e1748-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1748-119">Element</span></span>|<span data-ttu-id="e1748-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="e1748-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1748-121">Elemento ListEntry para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e1748-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="e1748-122">Proporciona una definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e1748-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1748-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e1748-123">Remarks</span></span>

<span data-ttu-id="e1748-124">Para obtener más información acerca de este tipo de vista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e1748-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1748-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e1748-125">Example</span></span>

<span data-ttu-id="e1748-126">En este ejemplo se muestran los elementos XML que definen tres filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e1748-126">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="e1748-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="e1748-127">See Also</span></span>

[<span data-ttu-id="e1748-128">Elemento ListEntry para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e1748-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="e1748-129">Elemento ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e1748-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e1748-130">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="e1748-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e1748-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1748-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
