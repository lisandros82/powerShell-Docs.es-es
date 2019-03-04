---
title: Elemento FirstLineHanging para el marco de control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ae4ad8ae3e6cb5d1174dc001b30aa84dd182a606
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860241"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="db38c-102">Elemento FirstLineHanging para Frame for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="db38c-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="db38c-103">Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="db38c-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="db38c-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="db38c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="db38c-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para elemento de marco de CutomControlView (formato) de CustomItem para el control personalizado de vista (formato) FirstLineHanging del elemento de marco para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="db38c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db38c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="db38c-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db38c-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="db38c-107">Attributes and Elements</span></span>

<span data-ttu-id="db38c-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="db38c-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db38c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="db38c-109">Attributes</span></span>

<span data-ttu-id="db38c-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="db38c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db38c-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="db38c-111">Child Elements</span></span>

<span data-ttu-id="db38c-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="db38c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="db38c-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="db38c-113">Parent Elements</span></span>

|<span data-ttu-id="db38c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="db38c-114">Element</span></span>|<span data-ttu-id="db38c-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="db38c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db38c-116">Elemento de marco para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="db38c-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="db38c-117">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="db38c-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="db38c-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="db38c-118">Text Value</span></span>

<span data-ttu-id="db38c-119">Especifique el número de caracteres que se desean desplazar la primera línea de los datos.</span><span class="sxs-lookup"><span data-stu-id="db38c-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="db38c-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="db38c-120">Remarks</span></span>

<span data-ttu-id="db38c-121">Si se especifica este elemento, no se puede especificar el [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="db38c-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="db38c-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="db38c-122">See Also</span></span>

[<span data-ttu-id="db38c-123">Elemento FirstLineIndent marco para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="db38c-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db38c-124">Elemento de marco para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="db38c-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db38c-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="db38c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
