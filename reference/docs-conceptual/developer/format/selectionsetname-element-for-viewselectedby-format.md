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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368264"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="b6949-102">Elemento SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b6949-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="b6949-103">Especifica un conjunto de objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="b6949-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="b6949-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ViewSelectedBy (Format) elemento SelectionSetName para ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b6949-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6949-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b6949-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6949-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b6949-106">Attributes and Elements</span></span>

<span data-ttu-id="b6949-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="b6949-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6949-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6949-108">Attributes</span></span>

<span data-ttu-id="b6949-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b6949-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6949-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b6949-110">Child Elements</span></span>

<span data-ttu-id="b6949-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b6949-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6949-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b6949-112">Parent Elements</span></span>

|<span data-ttu-id="b6949-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6949-113">Element</span></span>|<span data-ttu-id="b6949-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="b6949-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6949-115">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b6949-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="b6949-116">Define los objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="b6949-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6949-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b6949-117">Text Value</span></span>

<span data-ttu-id="b6949-118">Especifique el nombre del conjunto de selección definido por el elemento `Name` para el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="b6949-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6949-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b6949-119">Remarks</span></span>

<span data-ttu-id="b6949-120">Puede usar conjuntos de selección cuando tiene un conjunto de objetos relacionados a los que desea hacer referencia mediante un nombre único, como un conjunto de objetos que se relacionan a través de la herencia.</span><span class="sxs-lookup"><span data-stu-id="b6949-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="b6949-121">Para obtener más información sobre cómo definir y hacer referencia a conjuntos de selección, vea [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b6949-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="b6949-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b6949-122">Example</span></span>

<span data-ttu-id="b6949-123">En el ejemplo siguiente se muestra cómo especificar un conjunto de selección para una vista de lista.</span><span class="sxs-lookup"><span data-stu-id="b6949-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="b6949-124">Se usa el mismo esquema para las vistas de tabla, ancho y personalizado.</span><span class="sxs-lookup"><span data-stu-id="b6949-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="b6949-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="b6949-125">See Also</span></span>

[<span data-ttu-id="b6949-126">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="b6949-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b6949-127">Elemento ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b6949-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="b6949-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6949-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
