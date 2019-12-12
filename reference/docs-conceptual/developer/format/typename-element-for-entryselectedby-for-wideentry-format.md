---
title: Elemento TypeName para EntrySelectedBy para WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361624"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="5c05e-102">Elemento TypeName para EntrySelectedBy for WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5c05e-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="5c05e-103">Especifica un tipo .NET para la definición.</span><span class="sxs-lookup"><span data-stu-id="5c05e-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="5c05e-104">La definición se usa siempre que se muestra este objeto.</span><span class="sxs-lookup"><span data-stu-id="5c05e-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="5c05e-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry (Format) EntrySelectedBy Element for WideEntry (Format) TypeName for WideEntry ( Aplique</span><span class="sxs-lookup"><span data-stu-id="5c05e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c05e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5c05e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c05e-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="5c05e-107">Attributes and Elements</span></span>

<span data-ttu-id="5c05e-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="5c05e-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c05e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5c05e-109">Attributes</span></span>

<span data-ttu-id="5c05e-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5c05e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c05e-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="5c05e-111">Child Elements</span></span>

<span data-ttu-id="5c05e-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5c05e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c05e-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="5c05e-113">Parent Elements</span></span>

|<span data-ttu-id="5c05e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c05e-114">Element</span></span>|<span data-ttu-id="5c05e-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="5c05e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c05e-116">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5c05e-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="5c05e-117">Define los tipos de .NET que usan esta entrada ancha o la condición que debe existir para que se use esta entrada.</span><span class="sxs-lookup"><span data-stu-id="5c05e-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5c05e-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5c05e-118">Text Value</span></span>

<span data-ttu-id="5c05e-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="5c05e-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c05e-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5c05e-120">Remarks</span></span>

<span data-ttu-id="5c05e-121">Cada entrada ancha debe especificar uno o varios tipos .NET, un conjunto de selección o la condición de selección que debe existir para que se use la definición.</span><span class="sxs-lookup"><span data-stu-id="5c05e-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="5c05e-122">Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5c05e-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5c05e-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="5c05e-123">See Also</span></span>

[<span data-ttu-id="5c05e-124">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="5c05e-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5c05e-125">Elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5c05e-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="5c05e-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c05e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
