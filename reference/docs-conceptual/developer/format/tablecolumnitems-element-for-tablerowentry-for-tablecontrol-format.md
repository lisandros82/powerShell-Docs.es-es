---
title: Elemento TableColumnItems para TableRowEntry para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361814"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="4428e-102">Elemento TableColumnItems para TableRowEntry for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4428e-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="4428e-103">Define las propiedades o los scripts cuyos valores se muestran en una fila.</span><span class="sxs-lookup"><span data-stu-id="4428e-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="4428e-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries para Tablecontrol ((Format) elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format) Elemento TableColumnItems para TableControlEntry para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="4428e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4428e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4428e-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4428e-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4428e-106">Attributes and Elements</span></span>

<span data-ttu-id="4428e-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableColumnItems`.</span><span class="sxs-lookup"><span data-stu-id="4428e-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4428e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="4428e-108">Attributes</span></span>

<span data-ttu-id="4428e-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4428e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4428e-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4428e-110">Child Elements</span></span>

|<span data-ttu-id="4428e-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="4428e-111">Element</span></span>|<span data-ttu-id="4428e-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="4428e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4428e-113">Elemento TableColumnItem para TableColumnItems para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="4428e-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="4428e-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="4428e-114">Required element.</span></span><br /><br /> <span data-ttu-id="4428e-115">Define la propiedad o el script cuyo valor se muestra en una columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="4428e-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4428e-116">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4428e-116">Parent Elements</span></span>

|<span data-ttu-id="4428e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4428e-117">Element</span></span>|<span data-ttu-id="4428e-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="4428e-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4428e-119">Elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="4428e-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="4428e-120">Define los datos que se muestran en una fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="4428e-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4428e-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4428e-121">Remarks</span></span>

<span data-ttu-id="4428e-122">Se requiere un elemento `TableColumnItem` para cada columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="4428e-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="4428e-123">La primera entrada se muestra en la primera columna, la segunda entrada de la segunda columna, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="4428e-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="4428e-124">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="4428e-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4428e-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4428e-125">Example</span></span>

<span data-ttu-id="4428e-126">En el ejemplo siguiente se muestra un elemento `TableColumnItems` que define tres propiedades del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="4428e-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4428e-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="4428e-127">See Also</span></span>

[<span data-ttu-id="4428e-128">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="4428e-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4428e-129">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4428e-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="4428e-130">Elemento TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4428e-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="4428e-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4428e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
