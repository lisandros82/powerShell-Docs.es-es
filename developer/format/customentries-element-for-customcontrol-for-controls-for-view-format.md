---
title: Elemento CustomEntries para el control personalizado para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066590"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="aa224-102">Elemento CustomEntries para CustomControl for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="aa224-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="aa224-103">Proporciona las definiciones para el control.</span><span class="sxs-lookup"><span data-stu-id="aa224-103">Provides the definitions for the control.</span></span> <span data-ttu-id="aa224-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="aa224-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="aa224-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa224-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa224-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aa224-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa224-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="aa224-107">Attributes and Elements</span></span>

<span data-ttu-id="aa224-108">Las secciones siguientes describen los atributos, elementos secundarios y elementos primarios de la `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="aa224-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="aa224-109">No hay ningún límite máximo para el número de elementos secundarios que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="aa224-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa224-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="aa224-110">Attributes</span></span>

<span data-ttu-id="aa224-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="aa224-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa224-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="aa224-112">Child Elements</span></span>

|<span data-ttu-id="aa224-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa224-113">Element</span></span>|<span data-ttu-id="aa224-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="aa224-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa224-115">Elemento CustomEntry para CustomEntries para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa224-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="aa224-116">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="aa224-116">Required element.</span></span><br /><br /> <span data-ttu-id="aa224-117">Proporciona una definición del control.</span><span class="sxs-lookup"><span data-stu-id="aa224-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aa224-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="aa224-118">Parent Elements</span></span>

|<span data-ttu-id="aa224-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa224-119">Element</span></span>|<span data-ttu-id="aa224-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="aa224-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa224-121">Elemento de control personalizado para el Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa224-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="aa224-122">Define el control utilizado por la vista.</span><span class="sxs-lookup"><span data-stu-id="aa224-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aa224-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="aa224-123">Remarks</span></span>

<span data-ttu-id="aa224-124">En la mayoría de los casos, un control tiene solo una definición, que se especifica en una sola `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="aa224-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="aa224-125">Sin embargo, es posible proporcionar varias definiciones si desea utilizar el mismo control para mostrar diferentes objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="aa224-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="aa224-126">En esos casos, puede definir un `CustomEntry` (elemento) para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="aa224-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa224-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="aa224-127">See Also</span></span>

[<span data-ttu-id="aa224-128">Elemento CustomEntry para CustomEntries para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa224-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="aa224-129">Elemento de control personalizado para el Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa224-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="aa224-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa224-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
