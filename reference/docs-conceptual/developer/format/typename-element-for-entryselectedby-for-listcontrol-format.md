---
title: Elemento TypeName para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361664"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="2a50b-102">Elemento TypeName para EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2a50b-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="2a50b-103">Especifica un tipo .NET que usa esta entrada de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="2a50b-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="2a50b-104">No hay ningún límite en el número de tipos que se pueden especificar para una entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="2a50b-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="2a50b-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries (Format) elemento ListEntry (Format) elemento EntrySelectedBy para ListEntry (Format) TypeName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2a50b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a50b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2a50b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a50b-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2a50b-107">Attributes and Elements</span></span>

<span data-ttu-id="2a50b-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="2a50b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a50b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a50b-109">Attributes</span></span>

<span data-ttu-id="2a50b-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2a50b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a50b-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2a50b-111">Child Elements</span></span>

<span data-ttu-id="2a50b-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2a50b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a50b-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2a50b-113">Parent Elements</span></span>

|<span data-ttu-id="2a50b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a50b-114">Element</span></span>|<span data-ttu-id="2a50b-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="2a50b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a50b-116">Elemento EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2a50b-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="2a50b-117">Define los tipos .NET que usan esta entrada de lista o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="2a50b-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a50b-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="2a50b-118">Text Value</span></span>

<span data-ttu-id="2a50b-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="2a50b-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a50b-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2a50b-120">Remarks</span></span>

<span data-ttu-id="2a50b-121">Cada entrada de la lista debe tener al menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="2a50b-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2a50b-122">Para obtener más información sobre cómo se usa este elemento en una vista de lista, vea [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2a50b-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2a50b-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2a50b-123">Example</span></span>

<span data-ttu-id="2a50b-124">En el ejemplo siguiente se muestra cómo especificar un conjunto de selección para una entrada de una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="2a50b-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="2a50b-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="2a50b-125">See Also</span></span>

[<span data-ttu-id="2a50b-126">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="2a50b-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2a50b-127">Elemento EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2a50b-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="2a50b-128">Elemento SelectionSetName para EntrySelectedBy para ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2a50b-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2a50b-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a50b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
