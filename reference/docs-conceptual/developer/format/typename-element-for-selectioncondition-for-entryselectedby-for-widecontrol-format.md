---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368064"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="57f9b-102">Elemento TypeName para SelectionCondition for EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="57f9b-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="57f9b-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="57f9b-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="57f9b-104">Cuando este tipo está presente, se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="57f9b-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="57f9b-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy para WideEntry (Format) elemento TypeName para SelectionCondition para EntrySelectedBy for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57f9b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57f9b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="57f9b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57f9b-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="57f9b-107">Attributes and Elements</span></span>

<span data-ttu-id="57f9b-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="57f9b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57f9b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="57f9b-109">Attributes</span></span>

<span data-ttu-id="57f9b-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="57f9b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57f9b-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="57f9b-111">Child Elements</span></span>

<span data-ttu-id="57f9b-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="57f9b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57f9b-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="57f9b-113">Parent Elements</span></span>

|<span data-ttu-id="57f9b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="57f9b-114">Element</span></span>|<span data-ttu-id="57f9b-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="57f9b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57f9b-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57f9b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="57f9b-117">Define la condición que debe existir para que se use esta entrada ancha.</span><span class="sxs-lookup"><span data-stu-id="57f9b-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57f9b-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="57f9b-118">Text Value</span></span>

<span data-ttu-id="57f9b-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="57f9b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="57f9b-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="57f9b-120">Remarks</span></span>

<span data-ttu-id="57f9b-121">La condición de selección puede especificar un tipo .NET o un conjunto de selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="57f9b-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="57f9b-122">Para obtener más información sobre cómo usar las condiciones de selección, consulte [definir condiciones para cuando se muestran los datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="57f9b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="57f9b-123">Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="57f9b-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57f9b-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="57f9b-124">See Also</span></span>

[<span data-ttu-id="57f9b-125">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="57f9b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="57f9b-126">Definir condiciones para el momento en que se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="57f9b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="57f9b-127">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57f9b-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="57f9b-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57f9b-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="57f9b-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="57f9b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
