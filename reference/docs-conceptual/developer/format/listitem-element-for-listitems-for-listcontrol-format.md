---
title: Elemento ListItem para ListItems para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365134"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="f22a7-102">Elemento ListItem para ListItems for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f22a7-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="f22a7-103">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f22a7-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="f22a7-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListControl (Format) elemento ListItems para ListControl (Format) ListItem para el elemento ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f22a7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f22a7-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f22a7-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f22a7-106">Attributes and Elements</span></span>

<span data-ttu-id="f22a7-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ListItem`.</span><span class="sxs-lookup"><span data-stu-id="f22a7-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="f22a7-108">Solo se puede especificar una propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="f22a7-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f22a7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f22a7-109">Attributes</span></span>

<span data-ttu-id="f22a7-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="f22a7-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f22a7-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f22a7-111">Child Elements</span></span>

|<span data-ttu-id="f22a7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f22a7-112">Element</span></span>|<span data-ttu-id="f22a7-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="f22a7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f22a7-114">Elemento FormatString para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f22a7-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f22a7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f22a7-116">Especifica una cadena de formato que define cómo se muestra el valor de la propiedad o del script.</span><span class="sxs-lookup"><span data-stu-id="f22a7-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="f22a7-117">Elemento ItemSelectionCondition para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f22a7-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f22a7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f22a7-119">Define la condición que debe existir para que se use este elemento de lista.</span><span class="sxs-lookup"><span data-stu-id="f22a7-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="f22a7-120">Elemento Label de ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f22a7-121">Elemento opcional</span><span class="sxs-lookup"><span data-stu-id="f22a7-121">Optional element</span></span><br /><br /> <span data-ttu-id="f22a7-122">Especifica la etiqueta que se muestra a la izquierda de la propiedad o del valor de script de la fila.</span><span class="sxs-lookup"><span data-stu-id="f22a7-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="f22a7-123">Elemento PropertyName para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f22a7-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f22a7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f22a7-125">Especifica la propiedad de .NET cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="f22a7-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="f22a7-126">Elemento ScriptBlock para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f22a7-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f22a7-127">Optional element.</span></span><br /><br /> <span data-ttu-id="f22a7-128">Especifica el script cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="f22a7-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f22a7-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f22a7-129">Parent Elements</span></span>

|<span data-ttu-id="f22a7-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="f22a7-130">Element</span></span>|<span data-ttu-id="f22a7-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="f22a7-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f22a7-132">Elemento ListItems para el control List (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f22a7-133">Define las propiedades y los scripts cuyos valores se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f22a7-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f22a7-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f22a7-134">Remarks</span></span>

<span data-ttu-id="f22a7-135">Para obtener más información sobre los componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f22a7-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f22a7-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f22a7-136">Example</span></span>

<span data-ttu-id="f22a7-137">En este ejemplo se muestran los elementos XML que definen tres filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f22a7-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="f22a7-138">Las dos primeras filas muestran el valor de una propiedad de .NET y la última fila muestra un valor generado por un script.</span><span class="sxs-lookup"><span data-stu-id="f22a7-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="f22a7-139">Véase también</span><span class="sxs-lookup"><span data-stu-id="f22a7-139">See Also</span></span>

[<span data-ttu-id="f22a7-140">ListItems (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f22a7-141">Elemento FormatString para ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f22a7-142">Elemento Label para ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f22a7-143">Elemento PropertyName para ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f22a7-144">Elemento ScriptBlock para ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f22a7-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f22a7-145">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="f22a7-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f22a7-146">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f22a7-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
