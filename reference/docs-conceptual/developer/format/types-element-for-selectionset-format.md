---
title: Elemento Types para SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367964"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="84393-102">Elemento Types para SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="84393-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="84393-103">Define los objetos .NET que se encuentran en el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="84393-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="84393-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento Types (Format)</span><span class="sxs-lookup"><span data-stu-id="84393-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84393-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="84393-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="84393-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="84393-106">Attributes and Elements</span></span>

<span data-ttu-id="84393-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Types`.</span><span class="sxs-lookup"><span data-stu-id="84393-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="84393-108">Debe haber al menos un elemento secundario, pero no hay ningún límite máximo para el número de elementos secundarios que se pueden agregar.</span><span class="sxs-lookup"><span data-stu-id="84393-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="84393-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="84393-109">Attributes</span></span>

<span data-ttu-id="84393-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="84393-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84393-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="84393-111">Child Elements</span></span>

|<span data-ttu-id="84393-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="84393-112">Element</span></span>|<span data-ttu-id="84393-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="84393-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84393-114">Elemento TypeName de Types (Format)</span><span class="sxs-lookup"><span data-stu-id="84393-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="84393-115">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="84393-115">Required element.</span></span><br /><br /> <span data-ttu-id="84393-116">Especifica el objeto .NET que pertenece al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="84393-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="84393-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="84393-117">Parent Elements</span></span>

|<span data-ttu-id="84393-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="84393-118">Element</span></span>|<span data-ttu-id="84393-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="84393-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84393-120">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="84393-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="84393-121">Define un conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="84393-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84393-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="84393-122">Remarks</span></span>

<span data-ttu-id="84393-123">Los objetos definidos por este elemento componen un conjunto de selección que se puede usar en una vista, mediante una definición de una vista (las vistas pueden tener varias definiciones) o cuando se especifica una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="84393-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="84393-124">Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="84393-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="84393-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="84393-125">Example</span></span>

<span data-ttu-id="84393-126">En este ejemplo se muestra un elemento `SelectionSet` que define cuatro tipos .NET.</span><span class="sxs-lookup"><span data-stu-id="84393-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="84393-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="84393-127">See Also</span></span>

[<span data-ttu-id="84393-128">Definir conjuntos de objetos</span><span class="sxs-lookup"><span data-stu-id="84393-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="84393-129">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="84393-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="84393-130">Elemento TypeName de Types (Format)</span><span class="sxs-lookup"><span data-stu-id="84393-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="84393-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84393-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
