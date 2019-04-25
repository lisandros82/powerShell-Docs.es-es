---
title: Elemento ListItems para ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065247"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="de34d-102">Elemento ListItems para ListEntry for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de34d-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="de34d-103">Define las propiedades y las secuencias de comandos cuyos valores se muestran en las filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="de34d-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="de34d-104">Configuración (formato) del elemento elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de elemento de lista (formato) del Control ListEntry para elemento de ListItems de ListControl (formato) de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de34d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de34d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="de34d-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de34d-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="de34d-106">Attributes and Elements</span></span>

<span data-ttu-id="de34d-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ListItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="de34d-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="de34d-108">No hay ningún límite al número de elementos secundarios que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="de34d-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="de34d-109">El orden de los elementos secundarios define el orden en que los valores se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="de34d-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="de34d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="de34d-110">Attributes</span></span>

<span data-ttu-id="de34d-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="de34d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de34d-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="de34d-112">Child Elements</span></span>

|<span data-ttu-id="de34d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="de34d-113">Element</span></span>|<span data-ttu-id="de34d-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="de34d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de34d-115">ListItem (elemento) para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de34d-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="de34d-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="de34d-116">Required element.</span></span><br /><br /> <span data-ttu-id="de34d-117">Define la propiedad o el script cuyo valor se muestra la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="de34d-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="de34d-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="de34d-118">Parent Elements</span></span>

|<span data-ttu-id="de34d-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="de34d-119">Element</span></span>|<span data-ttu-id="de34d-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="de34d-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de34d-121">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de34d-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="de34d-122">Proporciona una definición de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="de34d-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="de34d-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="de34d-123">Remarks</span></span>

<span data-ttu-id="de34d-124">Para obtener más información acerca de este tipo de vista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="de34d-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="de34d-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="de34d-125">Example</span></span>

<span data-ttu-id="de34d-126">Este ejemplo muestra los elementos XML que definen tres filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="de34d-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="de34d-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="de34d-127">See Also</span></span>

[<span data-ttu-id="de34d-128">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de34d-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="de34d-129">ListItem (elemento) para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="de34d-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="de34d-130">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="de34d-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="de34d-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de34d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
