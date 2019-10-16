---
title: Elemento SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368384"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="afcb0-102">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="afcb0-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="afcb0-103">Define un conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="afcb0-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="afcb0-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="afcb0-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afcb0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="afcb0-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afcb0-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="afcb0-106">Attributes and Elements</span></span>

<span data-ttu-id="afcb0-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSet`.</span><span class="sxs-lookup"><span data-stu-id="afcb0-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="afcb0-108">Cada conjunto de selección debe tener un nombre y debe especificar los objetos .NET del conjunto.</span><span class="sxs-lookup"><span data-stu-id="afcb0-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="afcb0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="afcb0-109">Attributes</span></span>

<span data-ttu-id="afcb0-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="afcb0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afcb0-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="afcb0-111">Child Elements</span></span>

|<span data-ttu-id="afcb0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="afcb0-112">Element</span></span>|<span data-ttu-id="afcb0-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="afcb0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afcb0-114">Elemento Name para SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="afcb0-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="afcb0-115">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="afcb0-115">Required element.</span></span><br /><br /> <span data-ttu-id="afcb0-116">Especifica el nombre usado para hacer referencia al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="afcb0-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="afcb0-117">Types (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="afcb0-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="afcb0-118">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="afcb0-118">Required element.</span></span><br /><br /> <span data-ttu-id="afcb0-119">Define los objetos .NET que se encuentran en el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="afcb0-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="afcb0-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="afcb0-120">Parent Elements</span></span>

|<span data-ttu-id="afcb0-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="afcb0-121">Element</span></span>|<span data-ttu-id="afcb0-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="afcb0-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afcb0-123">Formato del elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="afcb0-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="afcb0-124">Define los conjuntos comunes de objetos .NET que pueden ser utilizados por todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="afcb0-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="afcb0-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="afcb0-125">Remarks</span></span>

<span data-ttu-id="afcb0-126">Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia.</span><span class="sxs-lookup"><span data-stu-id="afcb0-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="afcb0-127">Al definir las vistas, puede especificar el conjunto de objetos mediante el nombre del conjunto de selección en lugar de enumerar todos los objetos de cada vista.</span><span class="sxs-lookup"><span data-stu-id="afcb0-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="afcb0-128">Los conjuntos de selección comunes se especifican por su nombre al definir las vistas del archivo de formato o las definiciones de las vistas.</span><span class="sxs-lookup"><span data-stu-id="afcb0-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="afcb0-129">En estos casos, el elemento secundario `SelectionSetName` de los elementos `ViewSelectedBy` y `EntrySelectedBy` especifica el conjunto que se va a utilizar.</span><span class="sxs-lookup"><span data-stu-id="afcb0-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="afcb0-130">Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="afcb0-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="afcb0-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="afcb0-131">Example</span></span>

<span data-ttu-id="afcb0-132">En el ejemplo siguiente se muestra un elemento `SelectionSet` que define cuatro tipos .NET.</span><span class="sxs-lookup"><span data-stu-id="afcb0-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="afcb0-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="afcb0-133">See Also</span></span>

[<span data-ttu-id="afcb0-134">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="afcb0-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="afcb0-135">Elemento Name de SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="afcb0-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="afcb0-136">Elemento SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="afcb0-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="afcb0-137">Types (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="afcb0-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="afcb0-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="afcb0-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
