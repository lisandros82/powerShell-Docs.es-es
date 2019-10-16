---
title: Elemento TableRowEntries para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368154"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="65b62-102">Elemento TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="65b62-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="65b62-103">Define las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="65b62-103">Defines the rows of the table.</span></span>

<span data-ttu-id="65b62-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="65b62-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65b62-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="65b62-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65b62-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="65b62-106">Attributes and Elements</span></span>

<span data-ttu-id="65b62-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TableRowEntries`.</span><span class="sxs-lookup"><span data-stu-id="65b62-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65b62-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="65b62-108">Attributes</span></span>

<span data-ttu-id="65b62-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="65b62-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65b62-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="65b62-110">Child Elements</span></span>

|<span data-ttu-id="65b62-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="65b62-111">Element</span></span>|<span data-ttu-id="65b62-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="65b62-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65b62-113">Elemento TableRowEntry para TableRowEntries para Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="65b62-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="65b62-114">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="65b62-114">Required element.</span></span><br /><br /> <span data-ttu-id="65b62-115">Define los datos que se muestran en una fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="65b62-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="65b62-116">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="65b62-116">Parent Elements</span></span>

|<span data-ttu-id="65b62-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="65b62-117">Element</span></span>|<span data-ttu-id="65b62-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="65b62-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65b62-119">Elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="65b62-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="65b62-120">Define un formato de tabla para una vista.</span><span class="sxs-lookup"><span data-stu-id="65b62-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="65b62-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="65b62-121">Remarks</span></span>

<span data-ttu-id="65b62-122">Debe especificar uno o varios elementos `TableRowEntry` para la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="65b62-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="65b62-123">No hay ningún límite máximo para el número de elementos `TableRowEntry` que se pueden agregar y su orden es significativo.</span><span class="sxs-lookup"><span data-stu-id="65b62-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="65b62-124">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="65b62-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="65b62-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="65b62-125">Example</span></span>

<span data-ttu-id="65b62-126">En el ejemplo siguiente se muestra un elemento `TableRowEntries` que define una fila que muestra los valores de dos propiedades del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="65b62-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="65b62-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="65b62-127">See Also</span></span>

[<span data-ttu-id="65b62-128">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="65b62-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="65b62-129">Elemento Tablecontrol ((Format)</span><span class="sxs-lookup"><span data-stu-id="65b62-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="65b62-130">Elemento TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="65b62-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="65b62-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="65b62-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
