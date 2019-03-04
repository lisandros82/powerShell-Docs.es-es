---
title: Elemento de control para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853731"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="c30fa-102">Elemento Control para Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="c30fa-103">Define un control que puede usar la vista y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="c30fa-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="c30fa-104">Elemento de vista de configuración (formato) del elemento elemento ViewDefinitions (formato) (formato) controla el elemento de Control de elemento (formato) para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c30fa-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c30fa-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c30fa-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="c30fa-106">Attributes and Elements</span></span>

<span data-ttu-id="c30fa-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="c30fa-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c30fa-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c30fa-108">Attributes</span></span>

<span data-ttu-id="c30fa-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="c30fa-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c30fa-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="c30fa-110">Child Elements</span></span>

|<span data-ttu-id="c30fa-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="c30fa-111">Element</span></span>|<span data-ttu-id="c30fa-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="c30fa-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c30fa-113">Nombre de elemento para el Control de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c30fa-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="c30fa-114">Required element.</span></span><br /><br /> <span data-ttu-id="c30fa-115">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="c30fa-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="c30fa-116">Elemento de control personalizado para el Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c30fa-117">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="c30fa-117">Required element.</span></span><br /><br /> <span data-ttu-id="c30fa-118">Define el control utilizado por esta vista.</span><span class="sxs-lookup"><span data-stu-id="c30fa-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c30fa-119">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="c30fa-119">Parent Elements</span></span>

|<span data-ttu-id="c30fa-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c30fa-120">Element</span></span>|<span data-ttu-id="c30fa-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="c30fa-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c30fa-122">Controls (elemento) (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="c30fa-123">Define los controles de vista que se pueden utilizar una vista específica.</span><span class="sxs-lookup"><span data-stu-id="c30fa-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c30fa-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c30fa-124">Remarks</span></span>

<span data-ttu-id="c30fa-125">Este control se puede especificar mediante los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="c30fa-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="c30fa-126">Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="c30fa-127">Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="c30fa-128">Elemento CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="c30fa-129">Elemento CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="c30fa-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="c30fa-130">See Also</span></span>

[<span data-ttu-id="c30fa-131">Elemento de control personalizado para el Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c30fa-132">Elemento CustomControlName para ExpressionBinding para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c30fa-133">Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c30fa-134">Elemento CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c30fa-135">Elemento CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c30fa-136">Controls (elemento) (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="c30fa-137">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="c30fa-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c30fa-138">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c30fa-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
