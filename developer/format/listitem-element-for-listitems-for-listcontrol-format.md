---
title: ListItem (elemento) para ListItems de ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065774"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="3f273-102">Elemento ListItem para ListItems for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="3f273-103">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3f273-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="3f273-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para el elemento ListItems de ListControl (formato) de ListControl (formato) ListItem para el elemento de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f273-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3f273-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f273-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3f273-106">Attributes and Elements</span></span>

<span data-ttu-id="3f273-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ListItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="3f273-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="3f273-108">Se puede especificar solo una propiedad o una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="3f273-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f273-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3f273-109">Attributes</span></span>

<span data-ttu-id="3f273-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="3f273-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f273-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3f273-111">Child Elements</span></span>

|<span data-ttu-id="3f273-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f273-112">Element</span></span>|<span data-ttu-id="3f273-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="3f273-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f273-114">Elemento FormatString para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3f273-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3f273-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3f273-116">Especifica una cadena de formato que define cómo se muestra el valor de propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="3f273-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="3f273-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3f273-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3f273-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3f273-119">Define la condición que debe cumplirse para que este elemento de lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="3f273-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="3f273-120">Elemento de etiqueta para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3f273-121">Elemento opcional</span><span class="sxs-lookup"><span data-stu-id="3f273-121">Optional element</span></span><br /><br /> <span data-ttu-id="3f273-122">Especifica la etiqueta que se muestra a la izquierda del valor de propiedad o un script en la fila.</span><span class="sxs-lookup"><span data-stu-id="3f273-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="3f273-123">Elemento PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3f273-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3f273-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3f273-125">Especifica la propiedad de .NET cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="3f273-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="3f273-126">Elemento de bloque de script para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3f273-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3f273-127">Optional element.</span></span><br /><br /> <span data-ttu-id="3f273-128">Especifica la secuencia de comandos cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="3f273-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3f273-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3f273-129">Parent Elements</span></span>

|<span data-ttu-id="3f273-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f273-130">Element</span></span>|<span data-ttu-id="3f273-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="3f273-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f273-132">Elemento ListItems para Control de lista (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="3f273-133">Define las propiedades y las secuencias de comandos cuyos valores se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3f273-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f273-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3f273-134">Remarks</span></span>

<span data-ttu-id="3f273-135">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3f273-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3f273-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3f273-136">Example</span></span>

<span data-ttu-id="3f273-137">Este ejemplo muestra los elementos XML que definen tres filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3f273-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="3f273-138">Las dos primeras filas mostrar el valor de una propiedad de .NET y la última fila muestra un valor generado por una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="3f273-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3f273-139">Véase también</span><span class="sxs-lookup"><span data-stu-id="3f273-139">See Also</span></span>

[<span data-ttu-id="3f273-140">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="3f273-141">Elemento FormatString para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3f273-142">Elemento de etiqueta para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3f273-143">Elemento PropertyName para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3f273-144">Elemento de bloque de script para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="3f273-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3f273-145">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="3f273-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3f273-146">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="3f273-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
