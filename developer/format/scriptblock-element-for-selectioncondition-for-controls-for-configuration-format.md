---
title: Elemento de bloque de script para SelectionCondition para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853221"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="f535b-102">Elemento ScriptBlock para SelectionCondition for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f535b-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f535b-103">Especifica la secuencia de comandos que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="f535b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f535b-104">Cuando se evalúa esta secuencia de comandos para `true`, se cumple la condición y se usa la definición.</span><span class="sxs-lookup"><span data-stu-id="f535b-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="f535b-105">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f535b-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f535b-106">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) EntrySelectedBy para CustomEntry para los controles de elemento de configuración (formato) SelectionCondition para EntrySelectedBy para los controles de configuración (formato) Elemento de bloque de script para SelectionCondition para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f535b-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f535b-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f535b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f535b-108">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f535b-108">Attributes and Elements</span></span>

<span data-ttu-id="f535b-109">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="f535b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f535b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f535b-110">Attributes</span></span>

<span data-ttu-id="f535b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f535b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f535b-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f535b-112">Child Elements</span></span>

<span data-ttu-id="f535b-113">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f535b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f535b-114">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f535b-114">Parent Elements</span></span>

|<span data-ttu-id="f535b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f535b-115">Element</span></span>|<span data-ttu-id="f535b-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="f535b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f535b-117">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f535b-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="f535b-118">Define una condición que debe cumplirse para que la definición de control comunes que se usará.</span><span class="sxs-lookup"><span data-stu-id="f535b-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f535b-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f535b-119">Text Value</span></span>

<span data-ttu-id="f535b-120">Especifique el script que se evalúa.</span><span class="sxs-lookup"><span data-stu-id="f535b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f535b-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f535b-121">Remarks</span></span>

<span data-ttu-id="f535b-122">La condición de selección debe especificar un nombre de la secuencia de comandos o la propiedad del uno menor para evaluar, pero no se pueden especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f535b-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f535b-123">Para obtener más información acerca de cómo se pueden utilizar condiciones de selección, consulte [definir condiciones para mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f535b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f535b-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="f535b-124">See Also</span></span>

[<span data-ttu-id="f535b-125">Elemento SelectionCondition para EntrySelectedBy para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f535b-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="f535b-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f535b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
