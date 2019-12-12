---
title: Elemento TypeName para EntrySelectedBy para Tablecontrol ((Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361634"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="83922-102">Elemento TypeName para EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="83922-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="83922-103">Especifica un tipo .NET que usa esta entrada de la vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="83922-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="83922-104">No hay ningún límite en el número de tipos que se pueden especificar para una entrada de tabla.</span><span class="sxs-lookup"><span data-stu-id="83922-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="83922-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Tablecontrol ((Format) elemento TableRowEntries (Format) TableRowEntry (Format) elemento EntrySelectedBy (Format) elemento TypeName para EntrySelectedBy para TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="83922-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83922-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="83922-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83922-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="83922-107">Attributes and Elements</span></span>

<span data-ttu-id="83922-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="83922-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83922-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="83922-109">Attributes</span></span>

<span data-ttu-id="83922-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="83922-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83922-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="83922-111">Child Elements</span></span>

<span data-ttu-id="83922-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="83922-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83922-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="83922-113">Parent Elements</span></span>

|<span data-ttu-id="83922-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="83922-114">Element</span></span>|<span data-ttu-id="83922-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="83922-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83922-116">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="83922-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="83922-117">Define los tipos .NET que usan esta entrada o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="83922-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="83922-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="83922-118">Text Value</span></span>

<span data-ttu-id="83922-119">Especifique el nombre del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="83922-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="83922-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="83922-120">Remarks</span></span>

<span data-ttu-id="83922-121">Cada entrada de la lista debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="83922-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="83922-122">Para obtener más información sobre los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="83922-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83922-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="83922-123">See Also</span></span>

[<span data-ttu-id="83922-124">Crear una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="83922-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="83922-125">Elemento EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="83922-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="83922-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="83922-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
