---
title: Elemento TableColumnItems para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056913"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="6a013-102">Elemento TableColumnItems para TableRowEntry for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6a013-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="6a013-103">Define las propiedades o scripts cuyos valores se muestran en una fila.</span><span class="sxs-lookup"><span data-stu-id="6a013-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="6a013-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuración (elemento) TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento TableColumnItems para TableControlEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6a013-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a013-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6a013-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a013-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="6a013-106">Attributes and Elements</span></span>

<span data-ttu-id="6a013-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableColumnItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="6a013-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a013-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6a013-108">Attributes</span></span>

<span data-ttu-id="6a013-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="6a013-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a013-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="6a013-110">Child Elements</span></span>

|<span data-ttu-id="6a013-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a013-111">Element</span></span>|<span data-ttu-id="6a013-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="6a013-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a013-113">Elemento TableColumnItem para TableColumnItems para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6a013-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="6a013-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="6a013-114">Required element.</span></span><br /><br /> <span data-ttu-id="6a013-115">Define la propiedad o el script cuyo valor se muestra en una columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="6a013-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a013-116">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="6a013-116">Parent Elements</span></span>

|<span data-ttu-id="6a013-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a013-117">Element</span></span>|<span data-ttu-id="6a013-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="6a013-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a013-119">Elemento TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="6a013-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="6a013-120">Define los datos que se muestran en una fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="6a013-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a013-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="6a013-121">Remarks</span></span>

<span data-ttu-id="6a013-122">Un `TableColumnItem` elemento es necesario para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="6a013-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="6a013-123">La primera entrada se muestra en la primera columna, la segunda entrada en la segunda y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="6a013-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="6a013-124">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6a013-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a013-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6a013-125">Example</span></span>

<span data-ttu-id="6a013-126">El ejemplo siguiente se muestra un `TableColumnItems` elemento que define tres propiedades de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="6a013-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="6a013-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="6a013-127">See Also</span></span>

[<span data-ttu-id="6a013-128">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="6a013-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6a013-129">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="6a013-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="6a013-130">Elemento TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="6a013-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="6a013-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a013-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
