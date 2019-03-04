---
title: Elemento CustomEntry para CustomEntries para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858781"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="ab4b4-102">Elemento CustomEntry para CustomEntries for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="ab4b4-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="ab4b4-103">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-103">Provides a definition of the control.</span></span> <span data-ttu-id="ab4b4-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ab4b4-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ab4b4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab4b4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ab4b4-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab4b4-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ab4b4-107">Attributes and Elements</span></span>

<span data-ttu-id="ab4b4-108">Las secciones siguientes describen los atributos, elementos secundarios y los elementos primarios de la `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab4b4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab4b4-109">Attributes</span></span>

<span data-ttu-id="ab4b4-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab4b4-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ab4b4-111">Child Elements</span></span>

|<span data-ttu-id="ab4b4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab4b4-112">Element</span></span>|<span data-ttu-id="ab4b4-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="ab4b4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab4b4-114">Elemento EntrySelectedBy para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ab4b4-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ab4b4-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ab4b4-116">Define los tipos de .NET que usan esta definición de control o la condición que debe existir para que esta definición para usarse.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ab4b4-117">Elemento CustomItem para CustomEntry para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ab4b4-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ab4b4-118">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-118">Required element.</span></span><br /><br /> <span data-ttu-id="ab4b4-119">Define cómo el control muestra los datos.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab4b4-120">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ab4b4-120">Parent Elements</span></span>

|<span data-ttu-id="ab4b4-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab4b4-121">Element</span></span>|<span data-ttu-id="ab4b4-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="ab4b4-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab4b4-123">Elemento CustomEntries para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ab4b4-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="ab4b4-124">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="ab4b4-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab4b4-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ab4b4-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ab4b4-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="ab4b4-126">See Also</span></span>

[<span data-ttu-id="ab4b4-127">Elemento CustomEntries para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="ab4b4-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ab4b4-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab4b4-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
