---
title: Elemento EntrySelectedBy para CustomEntry para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066301"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="ff5fe-102">Elemento EntrySelectedBy para CustomEntry for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ff5fe-103">Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que este control que se usará.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ff5fe-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ff5fe-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff5fe-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ff5fe-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff5fe-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="ff5fe-107">Attributes and Elements</span></span>

<span data-ttu-id="ff5fe-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff5fe-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff5fe-109">Attributes</span></span>

<span data-ttu-id="ff5fe-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff5fe-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="ff5fe-111">Child Elements</span></span>

|<span data-ttu-id="ff5fe-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff5fe-112">Element</span></span>|<span data-ttu-id="ff5fe-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="ff5fe-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff5fe-114">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ff5fe-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ff5fe-116">Define la condición que debe cumplirse para que la definición de control comunes que se usará.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="ff5fe-117">Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ff5fe-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ff5fe-119">Especifica un conjunto de tipos de .NET que usan esta definición del control común.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="ff5fe-120">Elemento TypeName para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ff5fe-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ff5fe-122">Especifica un tipo .NET que usa esta definición del control común.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff5fe-123">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="ff5fe-123">Parent Elements</span></span>

|<span data-ttu-id="ff5fe-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff5fe-124">Element</span></span>|<span data-ttu-id="ff5fe-125">Descripción</span><span class="sxs-lookup"><span data-stu-id="ff5fe-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff5fe-126">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="ff5fe-127">Proporciona una definición del control común.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff5fe-128">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ff5fe-128">Remarks</span></span>

<span data-ttu-id="ff5fe-129">Como mínimo, cada definición debe tener al menos un tipo. NET, conjunto de selección o condición de selección especificada.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="ff5fe-130">No hay ningún límite máximo para el número de tipos, conjuntos de selección o condiciones de selección que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="ff5fe-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff5fe-131">Véase también</span><span class="sxs-lookup"><span data-stu-id="ff5fe-131">See Also</span></span>

[<span data-ttu-id="ff5fe-132">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="ff5fe-133">Elemento SelectionSetName para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ff5fe-134">Elemento CustomEntry para el control personalizado para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="ff5fe-135">Elemento TypeName para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="ff5fe-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ff5fe-136">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff5fe-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
