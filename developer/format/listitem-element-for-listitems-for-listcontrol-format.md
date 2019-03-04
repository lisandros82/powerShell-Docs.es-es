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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855161"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="7a72e-102">Elemento ListItem para ListItems for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="7a72e-103">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7a72e-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="7a72e-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para el elemento ListItems de ListControl (formato) de ListControl (formato) ListItem para el elemento de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a72e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7a72e-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a72e-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7a72e-106">Attributes and Elements</span></span>

<span data-ttu-id="7a72e-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `ListItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="7a72e-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="7a72e-108">Se puede especificar solo una propiedad o una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="7a72e-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a72e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a72e-109">Attributes</span></span>

<span data-ttu-id="7a72e-110">Ninguno</span><span class="sxs-lookup"><span data-stu-id="7a72e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a72e-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7a72e-111">Child Elements</span></span>

|<span data-ttu-id="7a72e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a72e-112">Element</span></span>|<span data-ttu-id="7a72e-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="7a72e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a72e-114">Elemento FormatString para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="7a72e-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a72e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7a72e-116">Especifica una cadena de formato que define cómo se muestra el valor de propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="7a72e-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="7a72e-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="7a72e-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a72e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7a72e-119">Define la condición que debe cumplirse para que este elemento de lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="7a72e-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="7a72e-120">Elemento de etiqueta para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="7a72e-121">Elemento opcional</span><span class="sxs-lookup"><span data-stu-id="7a72e-121">Optional element</span></span><br /><br /> <span data-ttu-id="7a72e-122">Especifica la etiqueta que se muestra a la izquierda del valor de propiedad o un script en la fila.</span><span class="sxs-lookup"><span data-stu-id="7a72e-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="7a72e-123">Elemento PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="7a72e-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a72e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7a72e-125">Especifica la propiedad de .NET cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="7a72e-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="7a72e-126">Elemento de bloque de script para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="7a72e-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7a72e-127">Optional element.</span></span><br /><br /> <span data-ttu-id="7a72e-128">Especifica la secuencia de comandos cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="7a72e-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7a72e-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7a72e-129">Parent Elements</span></span>

|<span data-ttu-id="7a72e-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a72e-130">Element</span></span>|<span data-ttu-id="7a72e-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="7a72e-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a72e-132">Elemento ListItems para Control de lista (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="7a72e-133">Define las propiedades y las secuencias de comandos cuyos valores se muestran en la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7a72e-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7a72e-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7a72e-134">Remarks</span></span>

<span data-ttu-id="7a72e-135">Para obtener más información acerca de los componentes de una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7a72e-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7a72e-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7a72e-136">Example</span></span>

<span data-ttu-id="7a72e-137">Este ejemplo muestra los elementos XML que definen tres filas de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="7a72e-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="7a72e-138">Las dos primeras filas mostrar el valor de una propiedad de .NET y la última fila muestra un valor generado por una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="7a72e-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7a72e-139">Véase también</span><span class="sxs-lookup"><span data-stu-id="7a72e-139">See Also</span></span>

[<span data-ttu-id="7a72e-140">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="7a72e-141">Elemento FormatString para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="7a72e-142">Elemento de etiqueta para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="7a72e-143">Elemento PropertyName para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="7a72e-144">Elemento de bloque de script para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7a72e-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="7a72e-145">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="7a72e-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7a72e-146">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="7a72e-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
