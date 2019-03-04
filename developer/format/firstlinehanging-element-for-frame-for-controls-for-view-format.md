---
title: Elemento FirstLineHanging marco para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858721"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="55648-102">Elemento FirstLineHanging para Frame for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="55648-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="55648-103">Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="55648-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="55648-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="55648-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="55648-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de marco de vista (formato) para CustomItem para los controles de vista (formato) FirstLineHanging del elemento de Marco de controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="55648-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55648-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="55648-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55648-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="55648-107">Attributes and Elements</span></span>

<span data-ttu-id="55648-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="55648-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55648-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="55648-109">Attributes</span></span>

<span data-ttu-id="55648-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="55648-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55648-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="55648-111">Child Elements</span></span>

<span data-ttu-id="55648-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="55648-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55648-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="55648-113">Parent Elements</span></span>

|<span data-ttu-id="55648-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="55648-114">Element</span></span>|<span data-ttu-id="55648-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="55648-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55648-116">Elemento de marco para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="55648-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="55648-117">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="55648-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55648-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="55648-118">Text Value</span></span>

<span data-ttu-id="55648-119">Especifique el número de caracteres que se desean desplazar la primera línea de los datos.</span><span class="sxs-lookup"><span data-stu-id="55648-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="55648-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="55648-120">Remarks</span></span>

<span data-ttu-id="55648-121">Si se especifica este elemento, no se puede especificar el [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="55648-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="55648-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="55648-122">See Also</span></span>

[<span data-ttu-id="55648-123">Elemento FirstLineIndent marco para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="55648-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="55648-124">Elemento de marco para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="55648-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="55648-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="55648-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
