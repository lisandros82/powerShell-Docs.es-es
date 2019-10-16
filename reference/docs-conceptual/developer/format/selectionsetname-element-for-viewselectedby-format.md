---
title: Elemento SelectionSetName para ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368264"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="88e66-102">Elemento SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="88e66-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="88e66-103">Especifica un conjunto de objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="88e66-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="88e66-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento SelectionSetName para ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="88e66-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88e66-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="88e66-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88e66-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="88e66-106">Attributes and Elements</span></span>

<span data-ttu-id="88e66-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="88e66-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88e66-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="88e66-108">Attributes</span></span>

<span data-ttu-id="88e66-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="88e66-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88e66-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="88e66-110">Child Elements</span></span>

<span data-ttu-id="88e66-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="88e66-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88e66-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="88e66-112">Parent Elements</span></span>

|<span data-ttu-id="88e66-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="88e66-113">Element</span></span>|<span data-ttu-id="88e66-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="88e66-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88e66-115">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="88e66-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="88e66-116">Define los objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="88e66-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88e66-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="88e66-117">Text Value</span></span>

<span data-ttu-id="88e66-118">Especifique el nombre del conjunto de selección definido por el elemento `Name` para el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="88e66-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="88e66-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="88e66-119">Remarks</span></span>

<span data-ttu-id="88e66-120">Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia.</span><span class="sxs-lookup"><span data-stu-id="88e66-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="88e66-121">Para obtener más información sobre cómo definir y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="88e66-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="88e66-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="88e66-122">Example</span></span>

<span data-ttu-id="88e66-123">En el ejemplo siguiente se muestra cómo especificar un conjunto de selección para una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="88e66-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="88e66-124">Se usa el mismo esquema para las vistas de tabla, ancho y personalizado.</span><span class="sxs-lookup"><span data-stu-id="88e66-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="88e66-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="88e66-125">See Also</span></span>

[<span data-ttu-id="88e66-126">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="88e66-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="88e66-127">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="88e66-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="88e66-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="88e66-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
