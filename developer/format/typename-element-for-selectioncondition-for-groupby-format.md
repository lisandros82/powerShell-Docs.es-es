---
title: Elemento TypeName para SelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858811"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="588c8-102">Elemento TypeName para SelectionCondition for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="588c8-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="588c8-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="588c8-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="588c8-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="588c8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="588c8-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para GroupBy (formato) (elemento) SelectionCondition para EntrySelectedBy para TypeName GroupBy (formato) (elemento) para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="588c8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="588c8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="588c8-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="588c8-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="588c8-107">Attributes and Elements</span></span>

<span data-ttu-id="588c8-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="588c8-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="588c8-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="588c8-109">Attributes</span></span>

<span data-ttu-id="588c8-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="588c8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="588c8-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="588c8-111">Child Elements</span></span>

<span data-ttu-id="588c8-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="588c8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="588c8-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="588c8-113">Parent Elements</span></span>

|<span data-ttu-id="588c8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="588c8-114">Element</span></span>|<span data-ttu-id="588c8-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="588c8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="588c8-116">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="588c8-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="588c8-117">Define una condición que debe cumplirse para que se usará la definición del control.</span><span class="sxs-lookup"><span data-stu-id="588c8-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="588c8-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="588c8-118">Text Value</span></span>

<span data-ttu-id="588c8-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="588c8-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="588c8-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="588c8-120">Remarks</span></span>

<span data-ttu-id="588c8-121">Cuando se especifica este elemento, no puede especificar el `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="588c8-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="588c8-122">Para obtener más información acerca de cómo definir las condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="588c8-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="588c8-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="588c8-123">See Also</span></span>

[<span data-ttu-id="588c8-124">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="588c8-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="588c8-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="588c8-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
