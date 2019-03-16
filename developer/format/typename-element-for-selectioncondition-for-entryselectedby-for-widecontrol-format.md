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
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056014"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="0f4ab-102">Elemento TypeName para SelectionCondition for EntrySelectedBy for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4ab-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="0f4ab-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="0f4ab-104">Cuando este tipo está presente, se utiliza la definición.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="0f4ab-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuración para WideEntry (formato) SelectionCondition (elemento) para EntrySelectedBy para TypeName WideEntry (formato) (elemento) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4ab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f4ab-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0f4ab-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f4ab-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0f4ab-107">Attributes and Elements</span></span>

<span data-ttu-id="0f4ab-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f4ab-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f4ab-109">Attributes</span></span>

<span data-ttu-id="0f4ab-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f4ab-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0f4ab-111">Child Elements</span></span>

<span data-ttu-id="0f4ab-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f4ab-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0f4ab-113">Parent Elements</span></span>

|<span data-ttu-id="0f4ab-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f4ab-114">Element</span></span>|<span data-ttu-id="0f4ab-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="0f4ab-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f4ab-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4ab-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0f4ab-117">Define la condición que debe existir para que esta entrada amplia para usarse.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f4ab-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="0f4ab-118">Text Value</span></span>

<span data-ttu-id="0f4ab-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f4ab-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0f4ab-120">Remarks</span></span>

<span data-ttu-id="0f4ab-121">La condición de selección puede especificar un tipo de .NET o establece una selección, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="0f4ab-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando se muestran datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0f4ab-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0f4ab-123">Para obtener más información sobre otros componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f4ab-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f4ab-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="0f4ab-124">See Also</span></span>

[<span data-ttu-id="0f4ab-125">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="0f4ab-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0f4ab-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="0f4ab-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0f4ab-127">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4ab-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0f4ab-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4ab-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0f4ab-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f4ab-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
