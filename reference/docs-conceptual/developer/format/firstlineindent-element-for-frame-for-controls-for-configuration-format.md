---
title: Elemento FirstLineIndent para Frame para controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363124"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="1ac44-102">Elemento FirstLineIndent para Frame for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="1ac44-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1ac44-103">Especifica el número de caracteres que la primera línea de datos se desplaza hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="1ac44-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="1ac44-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="1ac44-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1ac44-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento CustomControl para el control de configuración (formato) elemento CustomEntries para CustomControl para la configuración ( Format) elemento CustomEntry para CustomControl en el caso de los controles para la configuración (Format) elemento CustomItem para CustomEntry para los controles de elemento de marco de configuración para CustomItem para los controles de configuración (Format) elemento FirstLineIndent para Frame para controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="1ac44-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ac44-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1ac44-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ac44-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1ac44-107">Attributes and Elements</span></span>

<span data-ttu-id="1ac44-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="1ac44-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ac44-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ac44-109">Attributes</span></span>

<span data-ttu-id="1ac44-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1ac44-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ac44-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1ac44-111">Child Elements</span></span>

<span data-ttu-id="1ac44-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="1ac44-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ac44-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1ac44-113">Parent Elements</span></span>

|<span data-ttu-id="1ac44-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ac44-114">Element</span></span>|<span data-ttu-id="1ac44-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="1ac44-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ac44-116">Elemento Frame para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="1ac44-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1ac44-117">Define cómo se muestran los datos, como el desplazamiento de los datos a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="1ac44-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ac44-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1ac44-118">Text Value</span></span>

<span data-ttu-id="1ac44-119">Especifique el número de caracteres que desea desplazar la primera línea de los datos.</span><span class="sxs-lookup"><span data-stu-id="1ac44-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ac44-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1ac44-120">Remarks</span></span>

<span data-ttu-id="1ac44-121">Si se especifica este elemento, no se puede especificar el elemento [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) .</span><span class="sxs-lookup"><span data-stu-id="1ac44-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ac44-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="1ac44-122">See Also</span></span>

[<span data-ttu-id="1ac44-123">Elemento FirstLineHanging para Frame para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="1ac44-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="1ac44-124">Elemento Frame para CustomItem para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="1ac44-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1ac44-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ac44-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
