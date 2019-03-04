---
title: Elemento SelectionSetName para ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858341"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="0d4dc-102">Elemento SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0d4dc-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="0d4dc-103">Especifica un conjunto de objetos .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="0d4dc-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ViewSelectedBy (formato) SelectionSetName elemento de configuración ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0d4dc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d4dc-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0d4dc-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d4dc-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0d4dc-106">Attributes and Elements</span></span>

<span data-ttu-id="0d4dc-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d4dc-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d4dc-108">Attributes</span></span>

<span data-ttu-id="0d4dc-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d4dc-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0d4dc-110">Child Elements</span></span>

<span data-ttu-id="0d4dc-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d4dc-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0d4dc-112">Parent Elements</span></span>

|<span data-ttu-id="0d4dc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d4dc-113">Element</span></span>|<span data-ttu-id="0d4dc-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d4dc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d4dc-115">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0d4dc-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="0d4dc-116">Define los objetos de .NET que se muestran en la vista.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0d4dc-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="0d4dc-117">Text Value</span></span>

<span data-ttu-id="0d4dc-118">Especifique el nombre del conjunto de selección que se define mediante el `Name` (elemento) para el conjunto de selección.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d4dc-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0d4dc-119">Remarks</span></span>

<span data-ttu-id="0d4dc-120">Puede usar conjuntos de selección cuando tenga un conjunto de objetos relacionados que desea hacer referencia mediante un nombre único, como un conjunto de objetos que están relacionadas mediante herencia.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="0d4dc-121">Para obtener más información sobre cómo definir y hacer referencia a conjuntos de selección, consulte [definir se establece los objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0d4dc-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d4dc-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d4dc-122">Example</span></span>

<span data-ttu-id="0d4dc-123">El ejemplo siguiente muestra cómo especificar una conjunto para obtener una vista de lista de selección.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="0d4dc-124">Se usa el mismo esquema para las vistas de tabla, amplia y personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0d4dc-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0d4dc-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="0d4dc-125">See Also</span></span>

[<span data-ttu-id="0d4dc-126">Definir conjuntos de selección</span><span class="sxs-lookup"><span data-stu-id="0d4dc-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0d4dc-127">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0d4dc-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="0d4dc-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d4dc-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
