---
title: Elemento Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363504"
---
# <a name="configuration-element-format"></a><span data-ttu-id="62177-102">Elemento Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="62177-102">Configuration Element (Format)</span></span>

<span data-ttu-id="62177-103">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="62177-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="62177-104">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="62177-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="62177-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="62177-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="62177-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="62177-106">Attributes and Elements</span></span>

<span data-ttu-id="62177-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="62177-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="62177-108">Este elemento debe ser el elemento raíz de cada archivo de formato y este elemento debe contener al menos un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="62177-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62177-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="62177-109">Attributes</span></span>

<span data-ttu-id="62177-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="62177-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62177-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="62177-111">Child Elements</span></span>

|<span data-ttu-id="62177-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="62177-112">Element</span></span>|<span data-ttu-id="62177-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="62177-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62177-114">Controls (elemento) para Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="62177-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="62177-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="62177-115">Optional element.</span></span><br /><br /> <span data-ttu-id="62177-116">Define los controles comunes que se pueden usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="62177-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="62177-117">DefaultSettings (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="62177-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="62177-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="62177-118">Optional element.</span></span><br /><br /> <span data-ttu-id="62177-119">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="62177-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="62177-120">Formato del elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="62177-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="62177-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="62177-121">Optional element.</span></span><br /><br /> <span data-ttu-id="62177-122">Define los conjuntos comunes de objetos .NET que pueden ser utilizados por todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="62177-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="62177-123">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="62177-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="62177-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="62177-124">Optional element.</span></span><br /><br /> <span data-ttu-id="62177-125">Define las vistas que se usan para mostrar los objetos.</span><span class="sxs-lookup"><span data-stu-id="62177-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="62177-126">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="62177-126">Parent Elements</span></span>

<span data-ttu-id="62177-127">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="62177-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="62177-128">Observaciones</span><span class="sxs-lookup"><span data-stu-id="62177-128">Remarks</span></span>

<span data-ttu-id="62177-129">Los archivos de formato definen cómo se muestran los objetos.</span><span class="sxs-lookup"><span data-stu-id="62177-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="62177-130">En la mayoría de los casos, este elemento raíz contiene un elemento [ViewDefinitions](./viewdefinitions-element-format.md) que define las vistas de tabla, lista y ancho del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="62177-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="62177-131">Además de las definiciones de vistas, el archivo de formato puede definir conjuntos de selección comunes, opciones y controles que estas vistas pueden utilizar.</span><span class="sxs-lookup"><span data-stu-id="62177-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="62177-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="62177-132">See Also</span></span>

[<span data-ttu-id="62177-133">Controls (elemento) para Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="62177-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="62177-134">DefaultSettings (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="62177-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="62177-135">Elemento SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="62177-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="62177-136">Elemento ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="62177-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="62177-137">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="62177-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
