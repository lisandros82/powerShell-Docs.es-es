---
title: Elemento DefaultSettings (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066352"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="5f6cd-102">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="5f6cd-103">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="5f6cd-104">Configuración común incluye presentación de errores, ajuste de texto en las tablas, definir cómo se expanden las colecciones y mucho más.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="5f6cd-105">Elemento de configuración (formato) elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5f6cd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5f6cd-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5f6cd-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="5f6cd-107">Attributes and Elements</span></span>

<span data-ttu-id="5f6cd-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `DefaultSettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5f6cd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f6cd-109">Attributes</span></span>

<span data-ttu-id="5f6cd-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5f6cd-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="5f6cd-111">Child Elements</span></span>

|<span data-ttu-id="5f6cd-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f6cd-112">Element</span></span>|<span data-ttu-id="5f6cd-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="5f6cd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f6cd-114">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="5f6cd-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5f6cd-116">Especifica que la cadena #ERR se muestra cuando se produce un error mientras se muestra un fragmento de datos.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="5f6cd-117">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="5f6cd-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5f6cd-119">Define las distintas formas en que los objetos de .NET se expanden cuando se muestran en una vista.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="5f6cd-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="5f6cd-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5f6cd-122">Especifica el número mínimo de propiedades que debe tener un objeto para mostrar el objeto en una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="5f6cd-123">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="5f6cd-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5f6cd-125">Especifica que el registro de error completo se muestra cuando se produce un error mientras se muestra un fragmento de datos.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="5f6cd-126">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="5f6cd-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-127">Optional element.</span></span><br /><br /> <span data-ttu-id="5f6cd-128">Especifica que los datos de una tabla se mueven a la línea siguiente si no cabe en el ancho de la columna.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5f6cd-129">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="5f6cd-129">Parent Elements</span></span>

|<span data-ttu-id="5f6cd-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f6cd-130">Element</span></span>|<span data-ttu-id="5f6cd-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="5f6cd-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f6cd-132">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="5f6cd-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="5f6cd-133">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f6cd-134">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5f6cd-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5f6cd-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="5f6cd-135">See Also</span></span>

[<span data-ttu-id="5f6cd-136">Elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="5f6cd-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="5f6cd-137">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="5f6cd-138">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="5f6cd-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="5f6cd-140">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="5f6cd-141">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="5f6cd-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="5f6cd-142">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f6cd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
