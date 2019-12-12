---
title: Elemento TypeName para SelectionCondition para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361614"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="61b03-102">Elemento TypeName para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="61b03-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="61b03-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="61b03-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="61b03-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="61b03-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="61b03-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para controles para Configuration (Format) elemento CustomEntry para CustomControl para controles de configuración (Format) elemento EntrySelectedBy para CustomEntry para controles de configuración (Format) elemento SelectionCondition para EntrySelectedBy para CustomEntry para Configuration (Format) elemento TypeName para SelectionCondition para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="61b03-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61b03-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="61b03-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="61b03-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="61b03-107">Attributes and Elements</span></span>

<span data-ttu-id="61b03-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="61b03-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61b03-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="61b03-109">Attributes</span></span>

<span data-ttu-id="61b03-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="61b03-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61b03-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="61b03-111">Child Elements</span></span>

<span data-ttu-id="61b03-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="61b03-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61b03-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="61b03-113">Parent Elements</span></span>

|<span data-ttu-id="61b03-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="61b03-114">Element</span></span>|<span data-ttu-id="61b03-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="61b03-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61b03-116">Elemento SelectionCondition para EntrySelectedBy para CustomEntry para Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="61b03-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="61b03-117">Define una condición que debe existir para que se use la definición de control.</span><span class="sxs-lookup"><span data-stu-id="61b03-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61b03-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="61b03-118">Text Value</span></span>

<span data-ttu-id="61b03-119">Especifique el nombre completo del tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="61b03-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="61b03-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="61b03-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="61b03-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="61b03-121">See Also</span></span>

[<span data-ttu-id="61b03-122">Elemento SelectionCondition para EntrySelectedBy para CustomEntry para Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="61b03-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="61b03-123">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="61b03-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
