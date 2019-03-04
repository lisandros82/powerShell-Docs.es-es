---
title: Elemento de control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861261"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="06e8e-102">Elemento CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="06e8e-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="06e8e-103">Define un formato de control personalizado para la vista.</span><span class="sxs-lookup"><span data-stu-id="06e8e-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="06e8e-104">Configuración elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento de control personalizado (formato)</span><span class="sxs-lookup"><span data-stu-id="06e8e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06e8e-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="06e8e-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06e8e-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="06e8e-106">Attributes and Elements</span></span>

<span data-ttu-id="06e8e-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="06e8e-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="06e8e-108">Debe especificar un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="06e8e-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06e8e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="06e8e-109">Attributes</span></span>

<span data-ttu-id="06e8e-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="06e8e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06e8e-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="06e8e-111">Child Elements</span></span>

|<span data-ttu-id="06e8e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="06e8e-112">Element</span></span>|<span data-ttu-id="06e8e-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="06e8e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06e8e-114">Elemento CustomEntries para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="06e8e-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="06e8e-115">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="06e8e-115">Required element.</span></span><br /><br /> <span data-ttu-id="06e8e-116">Proporciona las definiciones de la vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="06e8e-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06e8e-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="06e8e-117">Parent Elements</span></span>

|<span data-ttu-id="06e8e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="06e8e-118">Element</span></span>|<span data-ttu-id="06e8e-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="06e8e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06e8e-120">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="06e8e-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="06e8e-121">Define una vista que se usa para mostrar uno o varios objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="06e8e-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06e8e-122">Observaciones</span><span class="sxs-lookup"><span data-stu-id="06e8e-122">Remarks</span></span>

<span data-ttu-id="06e8e-123">En la mayoría de los casos, solo una definición es necesaria para cada vista de control, pero es posible proporcionar varias definiciones si desea usar la misma vista para mostrar diferentes objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="06e8e-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="06e8e-124">En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="06e8e-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="06e8e-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="06e8e-125">See Also</span></span>

[<span data-ttu-id="06e8e-126">Elemento CustomEntries para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="06e8e-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="06e8e-127">Elemento de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="06e8e-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="06e8e-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="06e8e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
