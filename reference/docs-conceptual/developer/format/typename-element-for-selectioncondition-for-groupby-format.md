---
title: Elemento TypeName para SelectionCondition para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361484"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="99071-102">Elemento TypeName para SelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="99071-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="99071-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="99071-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="99071-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="99071-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="99071-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para GroupBy (Format) elemento SelectionCondition para EntrySelectedBy para GroupBy (Format) elemento TypeName para SelectionCondition para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99071-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99071-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="99071-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="99071-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="99071-107">Attributes and Elements</span></span>

<span data-ttu-id="99071-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="99071-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99071-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="99071-109">Attributes</span></span>

<span data-ttu-id="99071-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="99071-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99071-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="99071-111">Child Elements</span></span>

<span data-ttu-id="99071-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="99071-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99071-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="99071-113">Parent Elements</span></span>

|<span data-ttu-id="99071-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="99071-114">Element</span></span>|<span data-ttu-id="99071-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="99071-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99071-116">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99071-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="99071-117">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="99071-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99071-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="99071-118">Text Value</span></span>

<span data-ttu-id="99071-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="99071-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="99071-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="99071-120">Remarks</span></span>

<span data-ttu-id="99071-121">Cuando se especifica este elemento, no se puede especificar el elemento `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="99071-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="99071-122">Para obtener más información sobre cómo definir condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99071-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99071-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="99071-123">See Also</span></span>

[<span data-ttu-id="99071-124">Elemento SelectionCondition para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99071-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="99071-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="99071-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
