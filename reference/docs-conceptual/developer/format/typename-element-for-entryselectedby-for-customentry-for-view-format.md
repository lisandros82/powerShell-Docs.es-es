---
title: Elemento TypeName para EntrySelectedBy para CustomEntry para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368074"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="029fa-102">Elemento TypeName para EntrySelectedBy for CustomEntry for View (formato)</span><span class="sxs-lookup"><span data-stu-id="029fa-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="029fa-103">Especifica un tipo .NET que usa esta definición de la vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="029fa-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="029fa-104">No hay ningún límite en el número de tipos que se pueden especificar para una definición.</span><span class="sxs-lookup"><span data-stu-id="029fa-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="029fa-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl (Format) elemento CustomEntries para CustomControl for View (Format) elemento CustomEntry para CustomEntries for View (Format) EntrySelectedBy Elemento para CustomEntry para el elemento TypeName de View (Format) para EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="029fa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="029fa-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="029fa-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="029fa-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="029fa-107">Attributes and Elements</span></span>

<span data-ttu-id="029fa-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="029fa-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="029fa-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="029fa-109">Attributes</span></span>

<span data-ttu-id="029fa-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="029fa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="029fa-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="029fa-111">Child Elements</span></span>

<span data-ttu-id="029fa-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="029fa-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="029fa-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="029fa-113">Parent Elements</span></span>

|<span data-ttu-id="029fa-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="029fa-114">Element</span></span>|<span data-ttu-id="029fa-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="029fa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="029fa-116">Elemento EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="029fa-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="029fa-117">Define los tipos .NET que usan esta definición de vista de control personalizada o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="029fa-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="029fa-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="029fa-118">Text Value</span></span>

<span data-ttu-id="029fa-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="029fa-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="029fa-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="029fa-120">Remarks</span></span>

<span data-ttu-id="029fa-121">Cada definición de vista de control personalizada debe tener por lo menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="029fa-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="029fa-122">Para obtener más información sobre los componentes de una vista de control personalizada, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="029fa-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="029fa-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="029fa-123">See Also</span></span>

[<span data-ttu-id="029fa-124">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="029fa-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="029fa-125">Elemento EntrySelectedBy para CustomEntry para View (Format)</span><span class="sxs-lookup"><span data-stu-id="029fa-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="029fa-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="029fa-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
