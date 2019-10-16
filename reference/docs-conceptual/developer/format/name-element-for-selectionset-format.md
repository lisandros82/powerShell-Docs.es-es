---
title: Elemento Name para SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362674"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="6ddd6-102">Elemento Name para SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="6ddd6-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="6ddd6-103">Especifica el nombre usado para hacer referencia al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="6ddd6-104">Elemento Configuration (Format) elemento SelectionSets (Format) elemento SelectionSet (Format) elemento Name de SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="6ddd6-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ddd6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6ddd6-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ddd6-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="6ddd6-106">Attributes and Elements</span></span>

<span data-ttu-id="6ddd6-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ddd6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6ddd6-108">Attributes</span></span>

<span data-ttu-id="6ddd6-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ddd6-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="6ddd6-110">Child Elements</span></span>

<span data-ttu-id="6ddd6-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ddd6-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="6ddd6-112">Parent Elements</span></span>

|<span data-ttu-id="6ddd6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ddd6-113">Element</span></span>|<span data-ttu-id="6ddd6-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="6ddd6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ddd6-115">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="6ddd6-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="6ddd6-116">Define un único conjunto de objetos .NET a los que se puede hacer referencia mediante el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ddd6-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="6ddd6-117">Text Value</span></span>

<span data-ttu-id="6ddd6-118">Especifique el nombre para hacer referencia al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="6ddd6-119">No hay restricciones en cuanto a los caracteres que se pueden usar.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ddd6-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="6ddd6-120">Remarks</span></span>

<span data-ttu-id="6ddd6-121">El nombre especificado aquí se usa en el elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="6ddd6-122">Conjunto de selección que se puede usar en una vista, mediante una definición de una vista (las vistas pueden tener varias definiciones) o cuando se especifica una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="6ddd6-123">Para obtener más información sobre los conjuntos de selección, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6ddd6-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ddd6-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6ddd6-124">Example</span></span>

<span data-ttu-id="6ddd6-125">En este ejemplo se muestra un elemento `SelectionSet` que define cuatro tipos .NET.</span><span class="sxs-lookup"><span data-stu-id="6ddd6-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="6ddd6-126">El nombre del conjunto de selección es "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="6ddd6-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6ddd6-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="6ddd6-127">See Also</span></span>

[<span data-ttu-id="6ddd6-128">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="6ddd6-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6ddd6-129">Elemento SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="6ddd6-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="6ddd6-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ddd6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
