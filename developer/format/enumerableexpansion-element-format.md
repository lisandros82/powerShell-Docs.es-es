---
title: Elemento EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066148"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="b1a59-102">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b1a59-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="b1a59-103">Define cómo determinados de .NET de colección, los objetos se expanden cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="b1a59-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="b1a59-104">Elemento EnumerableExpansions (formato) EnumerableExpansion elemento de configuración (formato) del elemento elemento DefaultSettings (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="b1a59-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1a59-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b1a59-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1a59-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b1a59-106">Attributes and Elements</span></span>

<span data-ttu-id="b1a59-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EnumerableExpansion` elemento.</span><span class="sxs-lookup"><span data-stu-id="b1a59-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1a59-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1a59-108">Attributes</span></span>

<span data-ttu-id="b1a59-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b1a59-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1a59-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b1a59-110">Child Elements</span></span>

|<span data-ttu-id="b1a59-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1a59-111">Element</span></span>|<span data-ttu-id="b1a59-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1a59-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1a59-113">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b1a59-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="b1a59-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b1a59-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b1a59-115">Define los objetos de colección de .NET se expanden por esta definición.</span><span class="sxs-lookup"><span data-stu-id="b1a59-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="b1a59-116">Expanda el elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="b1a59-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="b1a59-117">Especifica cómo se expande el objeto de colección para esta definición.</span><span class="sxs-lookup"><span data-stu-id="b1a59-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1a59-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b1a59-118">Parent Elements</span></span>

|<span data-ttu-id="b1a59-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1a59-119">Element</span></span>|<span data-ttu-id="b1a59-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1a59-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1a59-121">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="b1a59-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="b1a59-122">Define las diferentes formas de esa colección de .NET que los objetos se expanden cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="b1a59-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1a59-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b1a59-123">Remarks</span></span>

<span data-ttu-id="b1a59-124">Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="b1a59-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="b1a59-125">En este caso, un objeto de colección hace referencia a cualquier objeto que admita la **System.Collections.ICollection** interfaz.</span><span class="sxs-lookup"><span data-stu-id="b1a59-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="b1a59-126">El comportamiento predeterminado consiste en Mostrar solo las propiedades de los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="b1a59-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1a59-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="b1a59-127">See Also</span></span>

[<span data-ttu-id="b1a59-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b1a59-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
