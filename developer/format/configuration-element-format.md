---
title: Elemento de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856331"
---
# <a name="configuration-element-format"></a><span data-ttu-id="664b3-102">Elemento Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-102">Configuration Element (Format)</span></span>

<span data-ttu-id="664b3-103">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="664b3-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="664b3-104">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="664b3-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="664b3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="664b3-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="664b3-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="664b3-106">Attributes and Elements</span></span>

<span data-ttu-id="664b3-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Configuration` elemento.</span><span class="sxs-lookup"><span data-stu-id="664b3-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="664b3-108">Este elemento debe ser el elemento raíz de cada archivo de formato, y este elemento debe contener al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="664b3-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="664b3-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="664b3-109">Attributes</span></span>

<span data-ttu-id="664b3-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="664b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="664b3-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="664b3-111">Child Elements</span></span>

|<span data-ttu-id="664b3-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="664b3-112">Element</span></span>|<span data-ttu-id="664b3-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="664b3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="664b3-114">Controles de elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="664b3-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="664b3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="664b3-116">Define los controles comunes que pueden usarse en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="664b3-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="664b3-117">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="664b3-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="664b3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="664b3-119">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="664b3-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="664b3-120">Formato de elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="664b3-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="664b3-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="664b3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="664b3-122">Define los conjuntos comunes de objetos .NET que pueden usarse en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="664b3-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="664b3-123">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="664b3-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="664b3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="664b3-125">Define las vistas que se usa para mostrar los objetos.</span><span class="sxs-lookup"><span data-stu-id="664b3-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="664b3-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="664b3-126">Parent Elements</span></span>

<span data-ttu-id="664b3-127">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="664b3-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="664b3-128">Observaciones</span><span class="sxs-lookup"><span data-stu-id="664b3-128">Remarks</span></span>

<span data-ttu-id="664b3-129">Archivos de formato definen cómo se muestran los objetos.</span><span class="sxs-lookup"><span data-stu-id="664b3-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="664b3-130">En la mayoría de los casos, este elemento de raíz contiene un [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define la tabla, lista y vista amplia del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="664b3-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="664b3-131">Además de las definiciones de vista, puede definir el archivo de formato comunes conjuntos de selección, configuración y los controles que pueden usar dichas vistas.</span><span class="sxs-lookup"><span data-stu-id="664b3-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="664b3-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="664b3-132">See Also</span></span>

[<span data-ttu-id="664b3-133">Controles de elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="664b3-134">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="664b3-135">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="664b3-136">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="664b3-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="664b3-137">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="664b3-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
