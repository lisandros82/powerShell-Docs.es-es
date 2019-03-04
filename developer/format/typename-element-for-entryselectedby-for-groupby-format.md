---
title: Elemento TypeName para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861671"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="57204-102">Elemento TypeName para EntrySelectedBy for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="57204-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="57204-103">Especifica un tipo .NET que usa esta definición del control personalizado.</span><span class="sxs-lookup"><span data-stu-id="57204-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="57204-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="57204-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="57204-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) EntrySelectedBy para CustomEntry para TypeName GroupBy (formato) (elemento) para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="57204-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57204-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="57204-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57204-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="57204-107">Attributes and Elements</span></span>

<span data-ttu-id="57204-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="57204-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57204-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="57204-109">Attributes</span></span>

<span data-ttu-id="57204-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="57204-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57204-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="57204-111">Child Elements</span></span>

<span data-ttu-id="57204-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="57204-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57204-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="57204-113">Parent Elements</span></span>

|<span data-ttu-id="57204-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="57204-114">Element</span></span>|<span data-ttu-id="57204-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="57204-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57204-116">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="57204-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="57204-117">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="57204-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57204-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="57204-118">Text Value</span></span>

<span data-ttu-id="57204-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="57204-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="57204-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="57204-120">Remarks</span></span>

<span data-ttu-id="57204-121">Cada definición de control debe tener al menos un nombre de tipo, el conjunto de selección o condición de selección definida.</span><span class="sxs-lookup"><span data-stu-id="57204-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="57204-122">Para obtener más información acerca de los componentes de una vista de control personalizado, consulte [crear controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="57204-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57204-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="57204-123">See Also</span></span>

[<span data-ttu-id="57204-124">Creación de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="57204-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="57204-125">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="57204-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="57204-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="57204-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
