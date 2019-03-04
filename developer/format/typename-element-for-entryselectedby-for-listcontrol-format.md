---
title: Elemento TypeName para EntrySelectedBy de ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856111"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8e82d-102">Elemento TypeName para EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e82d-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8e82d-103">Especifica un tipo .NET que usa esta entrada de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="8e82d-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="8e82d-104">No hay ningún límite al número de tipos que se pueden especificar para una entrada de lista.</span><span class="sxs-lookup"><span data-stu-id="8e82d-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="8e82d-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuración para TypeName ListEntry (formato) (elemento) para EntrySelectedBy de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e82d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e82d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8e82d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e82d-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8e82d-107">Attributes and Elements</span></span>

<span data-ttu-id="8e82d-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8e82d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e82d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e82d-109">Attributes</span></span>

<span data-ttu-id="8e82d-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8e82d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e82d-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8e82d-111">Child Elements</span></span>

<span data-ttu-id="8e82d-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8e82d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e82d-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8e82d-113">Parent Elements</span></span>

|<span data-ttu-id="8e82d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e82d-114">Element</span></span>|<span data-ttu-id="8e82d-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8e82d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e82d-116">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8e82d-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="8e82d-117">Define los tipos de .NET que usan esta entrada de lista o la condición que debe existir para que esta entrada que se usará.</span><span class="sxs-lookup"><span data-stu-id="8e82d-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8e82d-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8e82d-118">Text Value</span></span>

<span data-ttu-id="8e82d-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="8e82d-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e82d-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8e82d-120">Remarks</span></span>

<span data-ttu-id="8e82d-121">Cada entrada de la lista debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="8e82d-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8e82d-122">Para obtener más información sobre cómo se usa este elemento en una vista de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e82d-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e82d-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8e82d-123">Example</span></span>

<span data-ttu-id="8e82d-124">El ejemplo siguiente muestra cómo especificar una conjunto para una entrada de una vista de lista de selección.</span><span class="sxs-lookup"><span data-stu-id="8e82d-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="8e82d-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="8e82d-125">See Also</span></span>

[<span data-ttu-id="8e82d-126">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="8e82d-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8e82d-127">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8e82d-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="8e82d-128">Elemento SelectionSetName para EnrtySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8e82d-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8e82d-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e82d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
