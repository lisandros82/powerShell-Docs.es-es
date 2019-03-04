---
title: Elemento de marco para CustomItem para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861711"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="4de31-102">Elemento Frame para CustomItem for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="4de31-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="4de31-103">Define cómo se muestran los datos, por ejemplo, cuando se desplaza los datos a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="4de31-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="4de31-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="4de31-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4de31-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) el elemento de control personalizado (formato) CustomEntries elemento de configuración control personalizado de vista (formato) del elemento CustomEntry para CustomEntries de vista (formato) del elemento CustomItem para CustomEntry para elemento de marco de CutomControlView (formato) de CustomItem para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4de31-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4de31-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4de31-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4de31-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4de31-107">Attributes and Elements</span></span>

<span data-ttu-id="4de31-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="4de31-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4de31-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4de31-109">Attributes</span></span>

<span data-ttu-id="4de31-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4de31-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4de31-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4de31-111">Child Elements</span></span>

|<span data-ttu-id="4de31-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4de31-112">Element</span></span>|<span data-ttu-id="4de31-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="4de31-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="4de31-114">Elemento necesario</span><span class="sxs-lookup"><span data-stu-id="4de31-114">Required Element</span></span>|
|[<span data-ttu-id="4de31-115">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="4de31-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4de31-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4de31-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4de31-117">Especifica cuántos caracteres de la primera línea de datos se desplaza a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="4de31-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="4de31-118">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="4de31-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4de31-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4de31-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4de31-120">Especifica cuántos caracteres de la primera línea de datos se desplaza a la derecha.</span><span class="sxs-lookup"><span data-stu-id="4de31-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="4de31-121">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="4de31-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4de31-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4de31-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4de31-123">Especifica cuántos caracteres de los datos se desplacen el margen izquierdo.</span><span class="sxs-lookup"><span data-stu-id="4de31-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="4de31-124">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="4de31-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4de31-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4de31-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4de31-126">Especifica cuántos caracteres de los datos se desplazan fuera del margen derecho.</span><span class="sxs-lookup"><span data-stu-id="4de31-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4de31-127">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4de31-127">Parent Elements</span></span>

|<span data-ttu-id="4de31-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="4de31-128">Element</span></span>|<span data-ttu-id="4de31-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="4de31-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4de31-130">Elemento CustomItem para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4de31-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="4de31-131">Define qué datos se muestran el control y cómo se muestran.</span><span class="sxs-lookup"><span data-stu-id="4de31-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4de31-132">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4de31-132">Remarks</span></span>

<span data-ttu-id="4de31-133">No puede especificar el [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) y [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos en la misma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="4de31-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4de31-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="4de31-134">See Also</span></span>

[<span data-ttu-id="4de31-135">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="4de31-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4de31-136">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="4de31-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4de31-137">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="4de31-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4de31-138">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="4de31-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4de31-139">Elemento CustomItem para CustomEntry para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="4de31-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4de31-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4de31-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
