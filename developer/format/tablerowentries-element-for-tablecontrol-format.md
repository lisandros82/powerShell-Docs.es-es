---
title: Elemento TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055740"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="75b50-102">Elemento TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="75b50-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="75b50-103">Define las filas de la tabla.</span><span class="sxs-lookup"><span data-stu-id="75b50-103">Defines the rows of the table.</span></span>

<span data-ttu-id="75b50-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuración TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="75b50-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75b50-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="75b50-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75b50-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="75b50-106">Attributes and Elements</span></span>

<span data-ttu-id="75b50-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `TableRowEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="75b50-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75b50-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="75b50-108">Attributes</span></span>

<span data-ttu-id="75b50-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="75b50-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75b50-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="75b50-110">Child Elements</span></span>

|<span data-ttu-id="75b50-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="75b50-111">Element</span></span>|<span data-ttu-id="75b50-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="75b50-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75b50-113">Elemento TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="75b50-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="75b50-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="75b50-114">Required element.</span></span><br /><br /> <span data-ttu-id="75b50-115">Define los datos que se muestran en una fila de la tabla.</span><span class="sxs-lookup"><span data-stu-id="75b50-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="75b50-116">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="75b50-116">Parent Elements</span></span>

|<span data-ttu-id="75b50-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="75b50-117">Element</span></span>|<span data-ttu-id="75b50-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="75b50-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75b50-119">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="75b50-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="75b50-120">Define un formato de tabla para obtener una vista.</span><span class="sxs-lookup"><span data-stu-id="75b50-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75b50-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="75b50-121">Remarks</span></span>

<span data-ttu-id="75b50-122">Debe especificar uno o varios `TableRowEntry` elementos de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="75b50-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="75b50-123">No hay ningún límite máximo para el número de `TableRowEntry` elementos que se pueden agregar ni su orden significativo.</span><span class="sxs-lookup"><span data-stu-id="75b50-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="75b50-124">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="75b50-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="75b50-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="75b50-125">Example</span></span>

<span data-ttu-id="75b50-126">El ejemplo siguiente se muestra un `TableRowEntries` elemento que define una fila que muestra los valores de las dos propiedades de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="75b50-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75b50-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="75b50-127">See Also</span></span>

[<span data-ttu-id="75b50-128">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="75b50-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="75b50-129">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="75b50-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="75b50-130">Elemento TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="75b50-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="75b50-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75b50-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
