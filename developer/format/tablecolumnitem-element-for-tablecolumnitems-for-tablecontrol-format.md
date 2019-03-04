---
title: Elemento TableColumnItem para TableColumnItems para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862421"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="eda5d-102">Elemento TableColumnItem para TableColumnItems for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="eda5d-103">Define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="eda5d-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="eda5d-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuración (elemento) TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento TableColumnItems para TableControlEntry para TableControl (formato) (elemento) TableColumnItem para TableColumnItems para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eda5d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="eda5d-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eda5d-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="eda5d-106">Attributes and Elements</span></span>

<span data-ttu-id="eda5d-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableColumnItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="eda5d-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eda5d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="eda5d-108">Attributes</span></span>

<span data-ttu-id="eda5d-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="eda5d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eda5d-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="eda5d-110">Child Elements</span></span>

|<span data-ttu-id="eda5d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="eda5d-111">Element</span></span>|<span data-ttu-id="eda5d-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="eda5d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eda5d-113">Elemento Alignment para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="eda5d-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eda5d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="eda5d-115">Define cómo se muestran los datos en una columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="eda5d-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="eda5d-116">Elemento FormatString para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="eda5d-117">Especifica un patrón de formato que se usa para dar formato a los datos de la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="eda5d-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="eda5d-118">Elemento PropertyName para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="eda5d-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eda5d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="eda5d-120">Especifica el nombre de la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="eda5d-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="eda5d-121">Elemento de bloque de script para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="eda5d-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="eda5d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="eda5d-123">Especifica la secuencia de comandos cuyo valor se muestra en la columna de una fila.</span><span class="sxs-lookup"><span data-stu-id="eda5d-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eda5d-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="eda5d-124">Parent Elements</span></span>

|<span data-ttu-id="eda5d-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="eda5d-125">Element</span></span>|<span data-ttu-id="eda5d-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="eda5d-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eda5d-127">Elemento TableColumnItems para TableControlEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="eda5d-128">Define las propiedades o scripts cuyos valores se muestran en la fila.</span><span class="sxs-lookup"><span data-stu-id="eda5d-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eda5d-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="eda5d-129">Remarks</span></span>

<span data-ttu-id="eda5d-130">Puede especificar una propiedad de un objeto o un script en cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="eda5d-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="eda5d-131">Si no hay elementos secundarios se especifican, el elemento es un marcador de posición, y no se muestra ningún dato.</span><span class="sxs-lookup"><span data-stu-id="eda5d-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="eda5d-132">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="eda5d-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="eda5d-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="eda5d-133">Example</span></span>

<span data-ttu-id="eda5d-134">Este ejemplo se muestra un `TableColumnItem` elemento que muestra el valor de la `Status` propiedad de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="eda5d-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="eda5d-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="eda5d-135">See Also</span></span>

[<span data-ttu-id="eda5d-136">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="eda5d-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="eda5d-137">Elemento Alignment para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="eda5d-138">Elemento TableColumnItems (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="eda5d-139">Elemento FormatString para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="eda5d-140">Elemento PropertyName para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="eda5d-141">Elemento de bloque de script para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="eda5d-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="eda5d-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eda5d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
