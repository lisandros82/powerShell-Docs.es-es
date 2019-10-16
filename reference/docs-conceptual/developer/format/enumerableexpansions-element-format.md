---
title: Elemento EnumerableExpansions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363304"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="4e300-102">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="4e300-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="4e300-103">Define cómo se expanden los objetos de la colección de .NET cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="4e300-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="4e300-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="4e300-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e300-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4e300-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e300-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4e300-106">Attributes and Elements</span></span>

<span data-ttu-id="4e300-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EnumerableExpansions`.</span><span class="sxs-lookup"><span data-stu-id="4e300-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="4e300-108">No hay ningún límite en el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="4e300-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e300-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4e300-109">Attributes</span></span>

<span data-ttu-id="4e300-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4e300-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e300-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4e300-111">Child Elements</span></span>

|<span data-ttu-id="4e300-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4e300-112">Element</span></span>|<span data-ttu-id="4e300-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="4e300-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e300-114">Elemento EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="4e300-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="4e300-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4e300-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4e300-116">Define los objetos de colección .NET específicos que se expanden cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="4e300-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e300-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4e300-117">Parent Elements</span></span>

|<span data-ttu-id="4e300-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="4e300-118">Element</span></span>|<span data-ttu-id="4e300-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="4e300-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e300-120">DefaultSettings (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="4e300-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="4e300-121">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="4e300-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e300-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4e300-122">Remarks</span></span>

<span data-ttu-id="4e300-123">Este elemento se utiliza para definir cómo se muestran los objetos de colección y los objetos de la colección.</span><span class="sxs-lookup"><span data-stu-id="4e300-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="4e300-124">En este caso, un objeto de colección hace referencia a cualquier objeto que admita la interfaz **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="4e300-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e300-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="4e300-125">See Also</span></span>

[<span data-ttu-id="4e300-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e300-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
