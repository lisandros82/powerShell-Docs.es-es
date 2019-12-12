---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361564"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="61e54-102">Elemento TypeName para SelectionCondition for EntrySelectedBy for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="61e54-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="61e54-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="61e54-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="61e54-104">Cuando este tipo está presente, se usa la entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="61e54-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="61e54-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListEntries para ListControl (Format) elemento EntrySelectedBy para ListEntry para ListControl (Format) elemento SelectionCondition para EntrySelectedBy para ListControl (Format) elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="61e54-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61e54-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="61e54-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61e54-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="61e54-107">Attributes and Elements</span></span>

<span data-ttu-id="61e54-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="61e54-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61e54-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="61e54-109">Attributes</span></span>

<span data-ttu-id="61e54-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="61e54-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61e54-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="61e54-111">Child Elements</span></span>

<span data-ttu-id="61e54-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="61e54-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61e54-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="61e54-113">Parent Elements</span></span>

|<span data-ttu-id="61e54-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="61e54-114">Element</span></span>|<span data-ttu-id="61e54-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="61e54-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61e54-116">Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="61e54-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="61e54-117">Define la condición que debe existir para que se use esta entrada de la lista.</span><span class="sxs-lookup"><span data-stu-id="61e54-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61e54-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="61e54-118">Text Value</span></span>

<span data-ttu-id="61e54-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="61e54-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="61e54-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="61e54-120">Remarks</span></span>

<span data-ttu-id="61e54-121">La condición de selección puede especificar cualquier número de tipos de .NET o conjuntos de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="61e54-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="61e54-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="61e54-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="61e54-123">Para obtener más información sobre otros componentes de una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="61e54-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61e54-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="61e54-124">See Also</span></span>

[<span data-ttu-id="61e54-125">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="61e54-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="61e54-126">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="61e54-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="61e54-127">Elemento SelectionCondition para EntrySelectedBy para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="61e54-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="61e54-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="61e54-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
