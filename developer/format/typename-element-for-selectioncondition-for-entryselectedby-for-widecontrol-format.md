---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 0d7bbfd8be3bf2bd1af75a45ca4db016dfb6bff6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857961"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ba4fd-102">Elemento TypeName para SelectionCondition for EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ba4fd-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ba4fd-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ba4fd-104">Cuando este tipo está presente, se utiliza la definición.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="ba4fd-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para TypeName WideEntry (formato) (elemento) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba4fd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba4fd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ba4fd-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba4fd-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ba4fd-107">Attributes and Elements</span></span>

<span data-ttu-id="ba4fd-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba4fd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba4fd-109">Attributes</span></span>

<span data-ttu-id="ba4fd-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ba4fd-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ba4fd-111">Child Elements</span></span>

<span data-ttu-id="ba4fd-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ba4fd-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ba4fd-113">Parent Elements</span></span>

|<span data-ttu-id="ba4fd-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba4fd-114">Element</span></span>|<span data-ttu-id="ba4fd-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="ba4fd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba4fd-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba4fd-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ba4fd-117">Define la condición que debe existir para que esta entrada amplia para usarse.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ba4fd-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ba4fd-118">Text Value</span></span>

<span data-ttu-id="ba4fd-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba4fd-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ba4fd-120">Remarks</span></span>

<span data-ttu-id="ba4fd-121">La condición de selección puede especificar un tipo de .NET o establece una selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ba4fd-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="ba4fd-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ba4fd-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ba4fd-123">Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ba4fd-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba4fd-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="ba4fd-124">See Also</span></span>

[<span data-ttu-id="ba4fd-125">Corrigió una vista amplia</span><span class="sxs-lookup"><span data-stu-id="ba4fd-125">Creatng a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ba4fd-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="ba4fd-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ba4fd-127">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba4fd-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ba4fd-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba4fd-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ba4fd-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba4fd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
