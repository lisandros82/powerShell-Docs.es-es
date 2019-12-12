---
title: Control (elemento) para controles de View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363474"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="79e09-102">Elemento Control para Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="79e09-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="79e09-103">Define un control que se puede usar en la vista y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="79e09-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="79e09-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Controls (Format) elemento control para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79e09-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="79e09-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79e09-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="79e09-106">Attributes and Elements</span></span>

<span data-ttu-id="79e09-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="79e09-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79e09-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="79e09-108">Attributes</span></span>

<span data-ttu-id="79e09-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="79e09-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79e09-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="79e09-110">Child Elements</span></span>

|<span data-ttu-id="79e09-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="79e09-111">Element</span></span>|<span data-ttu-id="79e09-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="79e09-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79e09-113">Elemento Name del control para la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="79e09-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="79e09-114">Required element.</span></span><br /><br /> <span data-ttu-id="79e09-115">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="79e09-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="79e09-116">Elemento CustomControl para el control de los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="79e09-117">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="79e09-117">Required element.</span></span><br /><br /> <span data-ttu-id="79e09-118">Define el control utilizado por esta vista.</span><span class="sxs-lookup"><span data-stu-id="79e09-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79e09-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="79e09-119">Parent Elements</span></span>

|<span data-ttu-id="79e09-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="79e09-120">Element</span></span>|<span data-ttu-id="79e09-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="79e09-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79e09-122">Controls (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="79e09-123">Define los controles de vista que se pueden usar en una vista específica.</span><span class="sxs-lookup"><span data-stu-id="79e09-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="79e09-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="79e09-124">Remarks</span></span>

<span data-ttu-id="79e09-125">Este control se puede especificar mediante los elementos siguientes:</span><span class="sxs-lookup"><span data-stu-id="79e09-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="79e09-126">Elemento CustomControlName para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="79e09-127">Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="79e09-128">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="79e09-129">Elemento CustomControlName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="79e09-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="79e09-130">See Also</span></span>

[<span data-ttu-id="79e09-131">Elemento CustomControl para el control de los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="79e09-132">Elemento CustomControlName para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="79e09-133">Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="79e09-134">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79e09-135">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79e09-136">Controls (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="79e09-137">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="79e09-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="79e09-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="79e09-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
