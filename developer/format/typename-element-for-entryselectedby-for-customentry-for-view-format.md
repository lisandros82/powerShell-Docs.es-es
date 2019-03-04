---
title: Elemento TypeName para EntrySelectedBy para CustomEntry para vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858841"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="41e76-102">Elemento TypeName para EntrySelectedBy for CustomEntry for View (formato)</span><span class="sxs-lookup"><span data-stu-id="41e76-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="41e76-103">Especifica un tipo .NET que usa esta definición de la vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="41e76-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="41e76-104">No hay ningún límite al número de tipos que se pueden especificar para una definición.</span><span class="sxs-lookup"><span data-stu-id="41e76-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="41e76-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para EntrySelectedBy vista (formato) Elemento para CustomEntry de vista (formato) del elemento TypeName para EntrySelectedBy para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="41e76-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41e76-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="41e76-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41e76-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="41e76-107">Attributes and Elements</span></span>

<span data-ttu-id="41e76-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="41e76-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41e76-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="41e76-109">Attributes</span></span>

<span data-ttu-id="41e76-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="41e76-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41e76-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="41e76-111">Child Elements</span></span>

<span data-ttu-id="41e76-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="41e76-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41e76-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="41e76-113">Parent Elements</span></span>

|<span data-ttu-id="41e76-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="41e76-114">Element</span></span>|<span data-ttu-id="41e76-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="41e76-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41e76-116">Elemento EntrySelectedBy para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="41e76-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="41e76-117">Define los tipos de .NET que utilizan esta definición de vista de control personalizado o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="41e76-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="41e76-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="41e76-118">Text Value</span></span>

<span data-ttu-id="41e76-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="41e76-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="41e76-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="41e76-120">Remarks</span></span>

<span data-ttu-id="41e76-121">Cada definición de la vista de control personalizado debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="41e76-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="41e76-122">Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="41e76-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41e76-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="41e76-123">See Also</span></span>

[<span data-ttu-id="41e76-124">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="41e76-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="41e76-125">Elemento EntrySelectedBy para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="41e76-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41e76-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="41e76-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
