---
title: Elemento PropertyName para TableColumnItem para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362254"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="3ae0a-102">Elemento PropertyName para TableColumnItem for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3ae0a-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="3ae0a-103">Especifica la propiedad cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="3ae0a-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="3ae0a-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento TableColumnItems (Format) elemento TableColumnItem (Format) Elemento PropertyName para TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="3ae0a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ae0a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3ae0a-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ae0a-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3ae0a-106">Attributes and Elements</span></span>

<span data-ttu-id="3ae0a-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3ae0a-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ae0a-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ae0a-108">Attributes</span></span>

<span data-ttu-id="3ae0a-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3ae0a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ae0a-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3ae0a-110">Child Elements</span></span>

<span data-ttu-id="3ae0a-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3ae0a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ae0a-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3ae0a-112">Parent Elements</span></span>

|<span data-ttu-id="3ae0a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ae0a-113">Element</span></span>|<span data-ttu-id="3ae0a-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="3ae0a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ae0a-115">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="3ae0a-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="3ae0a-116">Define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="3ae0a-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ae0a-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3ae0a-117">Text Value</span></span>

<span data-ttu-id="3ae0a-118">Especifique el nombre de la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="3ae0a-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ae0a-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3ae0a-119">Remarks</span></span>

<span data-ttu-id="3ae0a-120">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3ae0a-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3ae0a-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3ae0a-121">Example</span></span>

<span data-ttu-id="3ae0a-122">En este ejemplo se muestra un elemento `TableColumnItem` que especifica la propiedad `Status` del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="3ae0a-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="3ae0a-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="3ae0a-123">See Also</span></span>

[<span data-ttu-id="3ae0a-124">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="3ae0a-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3ae0a-125">Elemento TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="3ae0a-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="3ae0a-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ae0a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
