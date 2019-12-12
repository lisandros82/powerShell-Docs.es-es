---
title: Elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368774"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="f250e-102">Elemento EntrySelectedBy para CustomEntry for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f250e-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f250e-103">Define los tipos de .NET que usan la definición del control común o la condición que debe existir para que se utilice este control.</span><span class="sxs-lookup"><span data-stu-id="f250e-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f250e-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f250e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f250e-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f250e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f250e-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f250e-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f250e-107">Attributes and Elements</span></span>

<span data-ttu-id="f250e-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="f250e-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f250e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f250e-109">Attributes</span></span>

<span data-ttu-id="f250e-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f250e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f250e-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f250e-111">Child Elements</span></span>

|<span data-ttu-id="f250e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f250e-112">Element</span></span>|<span data-ttu-id="f250e-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="f250e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f250e-114">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="f250e-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f250e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f250e-116">Define la condición que debe existir para que se use la definición de control común.</span><span class="sxs-lookup"><span data-stu-id="f250e-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="f250e-117">Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f250e-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f250e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f250e-119">Especifica un conjunto de tipos de .NET que usan esta definición del control común.</span><span class="sxs-lookup"><span data-stu-id="f250e-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="f250e-120">Elemento TypeName para EntrySelectedBy para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="f250e-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f250e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f250e-122">Especifica un tipo .NET que usa esta definición del control común.</span><span class="sxs-lookup"><span data-stu-id="f250e-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f250e-123">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f250e-123">Parent Elements</span></span>

|<span data-ttu-id="f250e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f250e-124">Element</span></span>|<span data-ttu-id="f250e-125">Descripción</span><span class="sxs-lookup"><span data-stu-id="f250e-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f250e-126">Elemento CustomEntry para CustomControl para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="f250e-127">Proporciona una definición del control común.</span><span class="sxs-lookup"><span data-stu-id="f250e-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f250e-128">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f250e-128">Remarks</span></span>

<span data-ttu-id="f250e-129">Como mínimo, cada definición debe tener al menos un tipo de .NET, conjunto de selección o condición de selección especificada.</span><span class="sxs-lookup"><span data-stu-id="f250e-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="f250e-130">No hay ningún límite máximo para el número de tipos, conjuntos de selección o condiciones de selección que se pueden especificar.</span><span class="sxs-lookup"><span data-stu-id="f250e-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="f250e-131">Véase también</span><span class="sxs-lookup"><span data-stu-id="f250e-131">See Also</span></span>

[<span data-ttu-id="f250e-132">Elemento SelectionCondition de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="f250e-133">Elemento SelectionSetName de EntrySelectedBy para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f250e-134">Elemento CustomEntry para CustomControl para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="f250e-135">Elemento TypeName para EntrySelectedBy para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="f250e-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f250e-136">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f250e-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
