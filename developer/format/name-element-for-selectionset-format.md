---
title: Nombre de elemento para SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858171"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="f7cf2-102">Elemento Name para SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f7cf2-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="f7cf2-103">Especifica el nombre utilizado para hacer referencia el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="f7cf2-104">Elemento SelectionSet (formato) nombre elemento de configuración (formato) del elemento elemento SelectionSets (formato) de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f7cf2-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7cf2-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f7cf2-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7cf2-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f7cf2-106">Attributes and Elements</span></span>

<span data-ttu-id="f7cf2-107">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7cf2-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7cf2-108">Attributes</span></span>

<span data-ttu-id="f7cf2-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7cf2-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f7cf2-110">Child Elements</span></span>

<span data-ttu-id="f7cf2-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f7cf2-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f7cf2-112">Parent Elements</span></span>

|<span data-ttu-id="f7cf2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7cf2-113">Element</span></span>|<span data-ttu-id="f7cf2-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="f7cf2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7cf2-115">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f7cf2-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="f7cf2-116">Define un único conjunto de objetos .NET que se puede hacer referencia por el nombre del conjunto.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f7cf2-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f7cf2-117">Text Value</span></span>

<span data-ttu-id="f7cf2-118">Especifique el nombre que se hacen referencia al conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="f7cf2-119">Hay no hay restricciones en cuanto a qué caracteres se pueden usar.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7cf2-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f7cf2-120">Remarks</span></span>

<span data-ttu-id="f7cf2-121">El nombre especificado aquí se usa en el `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="f7cf2-122">El conjunto de selección que puede usar una vista, una definición de una vista (vistas pueden tener varias definiciones), o cuando se especifica una condición de selección.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="f7cf2-123">Para obtener más información acerca de los conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f7cf2-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f7cf2-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f7cf2-124">Example</span></span>

<span data-ttu-id="f7cf2-125">Este ejemplo se muestra un `SelectionSet` elemento que define cuatro tipos. NET.</span><span class="sxs-lookup"><span data-stu-id="f7cf2-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="f7cf2-126">El nombre del conjunto de selección es "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="f7cf2-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f7cf2-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="f7cf2-127">See Also</span></span>

[<span data-ttu-id="f7cf2-128">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="f7cf2-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f7cf2-129">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="f7cf2-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f7cf2-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7cf2-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
