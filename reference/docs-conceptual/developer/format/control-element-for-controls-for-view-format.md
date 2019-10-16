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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363474"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="daacc-102">Elemento Control para Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="daacc-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="daacc-103">Define un control que se puede usar en la vista y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="daacc-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="daacc-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento Controls (Format) elemento control para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="daacc-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="daacc-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="daacc-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="daacc-106">Attributes and Elements</span></span>

<span data-ttu-id="daacc-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Control`.</span><span class="sxs-lookup"><span data-stu-id="daacc-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="daacc-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="daacc-108">Attributes</span></span>

<span data-ttu-id="daacc-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="daacc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="daacc-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="daacc-110">Child Elements</span></span>

|<span data-ttu-id="daacc-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="daacc-111">Element</span></span>|<span data-ttu-id="daacc-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="daacc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="daacc-113">Elemento Name del control para la vista (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="daacc-114">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="daacc-114">Required element.</span></span><br /><br /> <span data-ttu-id="daacc-115">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="daacc-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="daacc-116">Elemento CustomControl para el control de los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="daacc-117">Elemento obligatorio.</span><span class="sxs-lookup"><span data-stu-id="daacc-117">Required element.</span></span><br /><br /> <span data-ttu-id="daacc-118">Define el control utilizado por esta vista.</span><span class="sxs-lookup"><span data-stu-id="daacc-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="daacc-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="daacc-119">Parent Elements</span></span>

|<span data-ttu-id="daacc-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="daacc-120">Element</span></span>|<span data-ttu-id="daacc-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="daacc-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="daacc-122">Controls (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="daacc-123">Define los controles de vista que se pueden usar en una vista específica.</span><span class="sxs-lookup"><span data-stu-id="daacc-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="daacc-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="daacc-124">Remarks</span></span>

<span data-ttu-id="daacc-125">Este control se puede especificar mediante los elementos siguientes:</span><span class="sxs-lookup"><span data-stu-id="daacc-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="daacc-126">Elemento CustomControlName para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="daacc-127">Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="daacc-128">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="daacc-129">Elemento CustomControlName para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="daacc-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="daacc-130">See Also</span></span>

[<span data-ttu-id="daacc-131">Elemento CustomControl para el control de los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="daacc-132">Elemento CustomControlName para ExpressionBinding para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="daacc-133">Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="daacc-134">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="daacc-135">Elemento CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="daacc-136">Controls (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="daacc-137">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="daacc-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="daacc-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="daacc-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
