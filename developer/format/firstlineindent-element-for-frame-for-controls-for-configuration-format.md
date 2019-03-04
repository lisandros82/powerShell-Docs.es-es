---
title: Elemento FirstLineIndent marco para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856351"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="60139-102">Elemento FirstLineIndent para Frame for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="60139-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="60139-103">Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="60139-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="60139-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="60139-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="60139-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de marco de configuración para CustomItem para los controles de elemento de configuración (formato) FirstLineIndent de marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="60139-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60139-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="60139-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60139-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="60139-107">Attributes and Elements</span></span>

<span data-ttu-id="60139-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="60139-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60139-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="60139-109">Attributes</span></span>

<span data-ttu-id="60139-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="60139-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60139-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="60139-111">Child Elements</span></span>

<span data-ttu-id="60139-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="60139-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60139-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="60139-113">Parent Elements</span></span>

|<span data-ttu-id="60139-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="60139-114">Element</span></span>|<span data-ttu-id="60139-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="60139-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60139-116">Elemento de marco para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="60139-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="60139-117">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="60139-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60139-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="60139-118">Text Value</span></span>

<span data-ttu-id="60139-119">Especifique el número de caracteres que se desean desplazar la primera línea de los datos.</span><span class="sxs-lookup"><span data-stu-id="60139-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="60139-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="60139-120">Remarks</span></span>

<span data-ttu-id="60139-121">Si se especifica este elemento, no se puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="60139-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="60139-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="60139-122">See Also</span></span>

[<span data-ttu-id="60139-123">Elemento FirstLineHanging marco para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="60139-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="60139-124">Elemento de marco para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="60139-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="60139-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="60139-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
