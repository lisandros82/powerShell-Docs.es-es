---
title: Elemento TypeName para tipos (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368034"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="505b8-102">Elemento TypeName para Types (formato)</span><span class="sxs-lookup"><span data-stu-id="505b8-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="505b8-103">Especifica el tipo .NET de un objeto que pertenece al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="505b8-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="505b8-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) Types (Format) elemento TypeName de Types (Format)</span><span class="sxs-lookup"><span data-stu-id="505b8-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="505b8-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="505b8-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="505b8-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="505b8-106">Attributes and Elements</span></span>

<span data-ttu-id="505b8-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="505b8-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="505b8-108">Debe incluirse al menos un elemento `TypeName` en el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="505b8-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="505b8-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="505b8-109">Attributes</span></span>

<span data-ttu-id="505b8-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="505b8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="505b8-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="505b8-111">Child Elements</span></span>

<span data-ttu-id="505b8-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="505b8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="505b8-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="505b8-113">Parent Elements</span></span>

|<span data-ttu-id="505b8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="505b8-114">Element</span></span>|<span data-ttu-id="505b8-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="505b8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="505b8-116">Types (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="505b8-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="505b8-117">Define los objetos .NET que se encuentran en el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="505b8-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="505b8-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="505b8-118">Text Value</span></span>

<span data-ttu-id="505b8-119">Especifique el nombre completo del tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="505b8-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="505b8-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="505b8-120">Remarks</span></span>

<span data-ttu-id="505b8-121">Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia.</span><span class="sxs-lookup"><span data-stu-id="505b8-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="505b8-122">Al definir las vistas, puede especificar el conjunto de objetos mediante el nombre del conjunto de selección en lugar de enumerar todos los objetos de cada vista.</span><span class="sxs-lookup"><span data-stu-id="505b8-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="505b8-123">Los conjuntos de selección comunes se especifican por su nombre al definir las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="505b8-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="505b8-124">En estos casos, el elemento secundario `SelectionSetName` del elemento `ViewSelectedBy` para la vista especifica el conjunto.</span><span class="sxs-lookup"><span data-stu-id="505b8-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="505b8-125">Sin embargo, las distintas entradas de una vista también pueden especificar un conjunto de selección que se aplique solo a esa entrada de la vista.</span><span class="sxs-lookup"><span data-stu-id="505b8-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="505b8-126">Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="505b8-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="505b8-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="505b8-127">Example</span></span>

<span data-ttu-id="505b8-128">En el ejemplo siguiente se muestra un elemento `SelectionSet` que define cuatro tipos .NET.</span><span class="sxs-lookup"><span data-stu-id="505b8-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="505b8-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="505b8-129">See Also</span></span>

[<span data-ttu-id="505b8-130">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="505b8-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="505b8-131">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="505b8-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="505b8-132">Elemento SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="505b8-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="505b8-133">Types (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="505b8-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="505b8-134">Escribir un archivo de formato de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="505b8-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
