---
title: Elemento EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368754"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="5ad98-102">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ad98-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="5ad98-103">Define cómo se expanden los objetos de colección .NET específicos cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="5ad98-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="5ad98-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5ad98-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ad98-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5ad98-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ad98-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="5ad98-106">Attributes and Elements</span></span>

<span data-ttu-id="5ad98-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EnumerableExpansion`.</span><span class="sxs-lookup"><span data-stu-id="5ad98-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ad98-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ad98-108">Attributes</span></span>

<span data-ttu-id="5ad98-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5ad98-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ad98-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="5ad98-110">Child Elements</span></span>

|<span data-ttu-id="5ad98-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ad98-111">Element</span></span>|<span data-ttu-id="5ad98-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="5ad98-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ad98-113">Elemento EntrySelectedBy para EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5ad98-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="5ad98-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ad98-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5ad98-115">Define qué objetos de colección .NET se expanden mediante esta definición.</span><span class="sxs-lookup"><span data-stu-id="5ad98-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="5ad98-116">Expand (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="5ad98-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="5ad98-117">Especifica cómo se expande el objeto de colección para esta definición.</span><span class="sxs-lookup"><span data-stu-id="5ad98-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ad98-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="5ad98-118">Parent Elements</span></span>

|<span data-ttu-id="5ad98-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ad98-119">Element</span></span>|<span data-ttu-id="5ad98-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="5ad98-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ad98-121">Elemento EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="5ad98-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="5ad98-122">Define las diferentes formas en que los objetos de colección de .NET se expanden cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="5ad98-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ad98-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5ad98-123">Remarks</span></span>

<span data-ttu-id="5ad98-124">Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="5ad98-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="5ad98-125">En este caso, un objeto de colección hace referencia a cualquier objeto que admita la interfaz **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="5ad98-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="5ad98-126">El comportamiento predeterminado es mostrar solo las propiedades de los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="5ad98-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ad98-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="5ad98-127">See Also</span></span>

[<span data-ttu-id="5ad98-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ad98-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)