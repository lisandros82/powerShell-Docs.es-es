---
title: Elemento FirstLineIndent marco para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065876"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="9a78c-102">Elemento FirstLineIndent para Frame for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="9a78c-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="9a78c-103">Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="9a78c-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="9a78c-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="9a78c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9a78c-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para elemento de marco de CustomControlView (formato) de CustomItem para el control personalizado de vista (formato) del elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="9a78c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="9a78c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9a78c-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a78c-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9a78c-107">Attributes and Elements</span></span>

<span data-ttu-id="9a78c-108">Las secciones siguientes describen los atributos, elementos secundarios y elemento primario de la `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="9a78c-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a78c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a78c-109">Attributes</span></span>

<span data-ttu-id="9a78c-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a78c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a78c-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9a78c-111">Child Elements</span></span>

<span data-ttu-id="9a78c-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a78c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a78c-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9a78c-113">Parent Elements</span></span>

|<span data-ttu-id="9a78c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a78c-114">Element</span></span>|<span data-ttu-id="9a78c-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="9a78c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a78c-116">Elemento de marco para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9a78c-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="9a78c-117">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="9a78c-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a78c-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9a78c-118">Text Value</span></span>

<span data-ttu-id="9a78c-119">Especifique el número de caracteres que se desean desplazar la primera línea de los datos.</span><span class="sxs-lookup"><span data-stu-id="9a78c-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a78c-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9a78c-120">Remarks</span></span>

<span data-ttu-id="9a78c-121">Si se especifica este elemento, no se puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9a78c-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a78c-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="9a78c-122">See Also</span></span>

[<span data-ttu-id="9a78c-123">Elemento FirstLineHanging para el marco de control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9a78c-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9a78c-124">Elemento de marco para CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9a78c-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9a78c-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a78c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
