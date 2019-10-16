---
title: Elemento TableColumnItem para TableColumnItems para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368234"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="fdcb7-102">Elemento TableColumnItem para TableColumnItems for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="fdcb7-103">Define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="fdcb7-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries para Tablecontrol ((Format) elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format) Elemento TableColumnItems para TableControlEntry para Tablecontrol ((Format) elemento TableColumnItem para TableColumnItems para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdcb7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fdcb7-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdcb7-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fdcb7-106">Attributes and Elements</span></span>

<span data-ttu-id="fdcb7-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableColumnItem`.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdcb7-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fdcb7-108">Attributes</span></span>

<span data-ttu-id="fdcb7-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdcb7-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fdcb7-110">Child Elements</span></span>

|<span data-ttu-id="fdcb7-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdcb7-111">Element</span></span>|<span data-ttu-id="fdcb7-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="fdcb7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdcb7-113">Elemento Alignment para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fdcb7-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-114">Optional element.</span></span><br /><br /> <span data-ttu-id="fdcb7-115">Define cómo se muestran los datos de una columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="fdcb7-116">Elemento FormatString para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fdcb7-117">Especifica un modelo de formato que se utiliza para dar formato a los datos de la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="fdcb7-118">Elemento PropertyName para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fdcb7-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fdcb7-120">Especifica el nombre de la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="fdcb7-121">Elemento ScriptBlock para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="fdcb7-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fdcb7-123">Especifica el script cuyo valor se muestra en la columna de una fila.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fdcb7-124">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fdcb7-124">Parent Elements</span></span>

|<span data-ttu-id="fdcb7-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdcb7-125">Element</span></span>|<span data-ttu-id="fdcb7-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="fdcb7-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdcb7-127">Elemento TableColumnItems para TableControlEntry para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fdcb7-128">Define las propiedades o los scripts cuyos valores se muestran en la fila.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fdcb7-129">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fdcb7-129">Remarks</span></span>

<span data-ttu-id="fdcb7-130">Puede especificar una propiedad de un objeto o un script en cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="fdcb7-131">Si no se especifica ningún elemento secundario, el elemento es un marcador de posición y no se muestra ningún dato.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="fdcb7-132">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fdcb7-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fdcb7-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fdcb7-133">Example</span></span>

<span data-ttu-id="fdcb7-134">En este ejemplo se muestra un elemento `TableColumnItem` que muestra el valor de la propiedad `Status` del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="fdcb7-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="fdcb7-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="fdcb7-135">See Also</span></span>

[<span data-ttu-id="fdcb7-136">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="fdcb7-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fdcb7-137">Elemento Alignment para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fdcb7-138">Elemento TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fdcb7-139">Elemento FormatString para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fdcb7-140">Elemento PropertyName para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fdcb7-141">Elemento ScriptBlock para TableColumnItem para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="fdcb7-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdcb7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
