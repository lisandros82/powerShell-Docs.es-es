---
title: Elemento TypeName para EntrySelectedBy para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361674"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="05952-102">Elemento TypeName para EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="05952-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="05952-103">Especifica un tipo .NET que usa esta definición del control personalizado.</span><span class="sxs-lookup"><span data-stu-id="05952-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="05952-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="05952-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="05952-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento EntrySelectedBy para CustomEntry para el elemento TypeName (Format) TypeName para EntrySelectedBy para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="05952-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05952-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="05952-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05952-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="05952-107">Attributes and Elements</span></span>

<span data-ttu-id="05952-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="05952-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05952-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="05952-109">Attributes</span></span>

<span data-ttu-id="05952-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="05952-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05952-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="05952-111">Child Elements</span></span>

<span data-ttu-id="05952-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="05952-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="05952-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="05952-113">Parent Elements</span></span>

|<span data-ttu-id="05952-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="05952-114">Element</span></span>|<span data-ttu-id="05952-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="05952-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05952-116">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="05952-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="05952-117">Define los tipos .NET que usan esta definición de control o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="05952-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="05952-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="05952-118">Text Value</span></span>

<span data-ttu-id="05952-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="05952-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="05952-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="05952-120">Remarks</span></span>

<span data-ttu-id="05952-121">Cada definición de control debe tener por lo menos un nombre de tipo, conjunto de selección o condición de selección definidos.</span><span class="sxs-lookup"><span data-stu-id="05952-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="05952-122">Para obtener más información sobre los componentes de una vista de control personalizada, vea [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="05952-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05952-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="05952-123">See Also</span></span>

[<span data-ttu-id="05952-124">Crear controles personalizados</span><span class="sxs-lookup"><span data-stu-id="05952-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="05952-125">Elemento EntrySelectedBy para CustomEntry para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="05952-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="05952-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="05952-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
