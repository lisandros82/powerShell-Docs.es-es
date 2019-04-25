---
title: Elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076317"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="142ef-102">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="142ef-103">Define un conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="142ef-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="142ef-104">Configuración (formato) elemento SelectionSets (formato) SelectionSet elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="142ef-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="142ef-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="142ef-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="142ef-106">Attributes and Elements</span></span>

<span data-ttu-id="142ef-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSet` elemento.</span><span class="sxs-lookup"><span data-stu-id="142ef-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="142ef-108">Cada conjunto de selección debe tener un nombre y debe especificar los objetos de .NET del conjunto.</span><span class="sxs-lookup"><span data-stu-id="142ef-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="142ef-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="142ef-109">Attributes</span></span>

<span data-ttu-id="142ef-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="142ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="142ef-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="142ef-111">Child Elements</span></span>

|<span data-ttu-id="142ef-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="142ef-112">Element</span></span>|<span data-ttu-id="142ef-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="142ef-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="142ef-114">Elemento Name de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="142ef-115">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="142ef-115">Required element.</span></span><br /><br /> <span data-ttu-id="142ef-116">Especifica el nombre utilizado para hacer referencia el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="142ef-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="142ef-117">Tipos de elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="142ef-118">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="142ef-118">Required element.</span></span><br /><br /> <span data-ttu-id="142ef-119">Define los objetos de .NET que están en la selección de conjunto.</span><span class="sxs-lookup"><span data-stu-id="142ef-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="142ef-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="142ef-120">Parent Elements</span></span>

|<span data-ttu-id="142ef-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="142ef-121">Element</span></span>|<span data-ttu-id="142ef-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="142ef-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="142ef-123">Formato de elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="142ef-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="142ef-124">Define los conjuntos comunes de objetos .NET que pueden usarse en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="142ef-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="142ef-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="142ef-125">Remarks</span></span>

<span data-ttu-id="142ef-126">Puede usar conjuntos de selección cuando tenga un conjunto de objetos relacionados que desea hacer referencia mediante un nombre único, como un conjunto de objetos que están relacionadas mediante herencia.</span><span class="sxs-lookup"><span data-stu-id="142ef-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="142ef-127">Al definir las vistas, puede especificar el conjunto de objetos con el nombre de la selección de conjunto en lugar de enumerar todos los objetos dentro de cada vista.</span><span class="sxs-lookup"><span data-stu-id="142ef-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="142ef-128">Al definir las vistas del archivo de formato o las definiciones de las vistas, se especifican conjuntos comunes de selección por su nombre.</span><span class="sxs-lookup"><span data-stu-id="142ef-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="142ef-129">En estos casos, el `SelectionSetName` elemento secundario de la `ViewSelectedBy` y `EntrySelectedBy` elementos especifica el conjunto que se usará.</span><span class="sxs-lookup"><span data-stu-id="142ef-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="142ef-130">Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="142ef-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="142ef-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="142ef-131">Example</span></span>

<span data-ttu-id="142ef-132">El ejemplo siguiente se muestra un `SelectionSet` elemento que define cuatro tipos. NET.</span><span class="sxs-lookup"><span data-stu-id="142ef-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="142ef-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="142ef-133">See Also</span></span>

[<span data-ttu-id="142ef-134">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="142ef-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="142ef-135">Elemento Name de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="142ef-136">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="142ef-137">Tipos de elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="142ef-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="142ef-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="142ef-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
