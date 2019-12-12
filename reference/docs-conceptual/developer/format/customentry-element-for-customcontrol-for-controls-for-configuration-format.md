---
title: Elemento CustomEntry para CustomControl para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364074"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="81dcc-102">Elemento CustomEntry para CustomControl for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="81dcc-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="81dcc-103">Proporciona una definición del control común.</span><span class="sxs-lookup"><span data-stu-id="81dcc-103">Provides a definition of the common control.</span></span> <span data-ttu-id="81dcc-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="81dcc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="81dcc-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="81dcc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81dcc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="81dcc-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="81dcc-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="81dcc-107">Attributes and Elements</span></span>

<span data-ttu-id="81dcc-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="81dcc-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="81dcc-109">Debe especificar los elementos que se muestran en la definición.</span><span class="sxs-lookup"><span data-stu-id="81dcc-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="81dcc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="81dcc-110">Attributes</span></span>

<span data-ttu-id="81dcc-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="81dcc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81dcc-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="81dcc-112">Child Elements</span></span>

|<span data-ttu-id="81dcc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="81dcc-113">Element</span></span>|<span data-ttu-id="81dcc-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="81dcc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81dcc-115">Elemento EntrySelectedBy de CustomEntry para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="81dcc-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="81dcc-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="81dcc-116">Optional element.</span></span><br /><br /> <span data-ttu-id="81dcc-117">Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="81dcc-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="81dcc-118">Elemento CustomItem de CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="81dcc-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="81dcc-119">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="81dcc-119">Required element.</span></span><br /><br /> <span data-ttu-id="81dcc-120">Define qué datos se muestran en el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="81dcc-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="81dcc-121">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="81dcc-121">Parent Elements</span></span>

|<span data-ttu-id="81dcc-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="81dcc-122">Element</span></span>|<span data-ttu-id="81dcc-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="81dcc-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81dcc-124">Elemento CustomEntries para CustomControl para Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="81dcc-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="81dcc-125">Proporciona las definiciones del control común.</span><span class="sxs-lookup"><span data-stu-id="81dcc-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="81dcc-126">Observaciones</span><span class="sxs-lookup"><span data-stu-id="81dcc-126">Remarks</span></span>

<span data-ttu-id="81dcc-127">En la mayoría de los casos, solo se requiere una definición para cada control personalizado común, pero es posible tener varias definiciones si se desea usar el mismo control para mostrar objetos .NET diferentes.</span><span class="sxs-lookup"><span data-stu-id="81dcc-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="81dcc-128">En esos casos, puede proporcionar una definición independiente para cada objeto o conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="81dcc-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="81dcc-129">Véase también</span><span class="sxs-lookup"><span data-stu-id="81dcc-129">See Also</span></span>

[<span data-ttu-id="81dcc-130">Elemento CustomEntries para CustomControl para Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="81dcc-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="81dcc-131">Elemento CustomItem de CustomEntry para controles de configuración</span><span class="sxs-lookup"><span data-stu-id="81dcc-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="81dcc-132">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="81dcc-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
