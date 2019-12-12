---
title: Expand (elemento, Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368744"
---
# <a name="expand-element-format"></a><span data-ttu-id="056f4-102">Elemento Expand (formato)</span><span class="sxs-lookup"><span data-stu-id="056f4-102">Expand Element (Format)</span></span>

<span data-ttu-id="056f4-103">Especifica cómo se expande el objeto de colección para esta definición.</span><span class="sxs-lookup"><span data-stu-id="056f4-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="056f4-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format) elemento EnumerableExpansion (Format) Expand Element (Format)</span><span class="sxs-lookup"><span data-stu-id="056f4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="056f4-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="056f4-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="056f4-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="056f4-106">Attributes and Elements</span></span>

<span data-ttu-id="056f4-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Expand`.</span><span class="sxs-lookup"><span data-stu-id="056f4-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="056f4-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="056f4-108">Attributes</span></span>

<span data-ttu-id="056f4-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="056f4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="056f4-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="056f4-110">Child Elements</span></span>

<span data-ttu-id="056f4-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="056f4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="056f4-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="056f4-112">Parent Elements</span></span>

|<span data-ttu-id="056f4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="056f4-113">Element</span></span>|<span data-ttu-id="056f4-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="056f4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="056f4-115">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="056f4-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="056f4-116">Define cómo se expanden los objetos de colección .NET específicos cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="056f4-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="056f4-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="056f4-117">Text Value</span></span>

<span data-ttu-id="056f4-118">Especifique uno de los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="056f4-118">Specify one of the following values:</span></span>

- <span data-ttu-id="056f4-119">EnumOnly: muestra solo las propiedades de los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="056f4-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="056f4-120">CoreOnly: muestra solo las propiedades del objeto de colección.</span><span class="sxs-lookup"><span data-stu-id="056f4-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="056f4-121">Both: muestra las propiedades de los objetos de la colección y las propiedades del objeto de colección.</span><span class="sxs-lookup"><span data-stu-id="056f4-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="056f4-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="056f4-122">Remarks</span></span>

<span data-ttu-id="056f4-123">Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="056f4-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="056f4-124">En este caso, un objeto de colección hace referencia a cualquier objeto que admita la interfaz **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="056f4-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="056f4-125">El comportamiento predeterminado es mostrar solo las propiedades de los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="056f4-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="056f4-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="056f4-126">See Also</span></span>

[<span data-ttu-id="056f4-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="056f4-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
