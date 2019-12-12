---
title: Elemento CustomControlName para ExpressionBinding para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368914"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="bf5f6-102">Elemento CustomControlName para ExpressionBinding for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="bf5f6-103">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="bf5f6-104">Este elemento se utiliza al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bf5f6-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento GroupBy para el elemento CustomControl para View (Format) para el elemento de GroupBy (Format) CustomEntries para CustomControl para el elemento CustomEntry de GroupBy (Format) para CustomControl para GroupBy (Format) elemento CustomItem para CustomEntry para el elemento ExpressionBinding GroupBy (Format) para CustomItem para GroupBy (Format) CustomControlName para ExpressionBinding para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf5f6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bf5f6-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf5f6-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="bf5f6-107">Attributes and Elements</span></span>

<span data-ttu-id="bf5f6-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf5f6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf5f6-109">Attributes</span></span>

<span data-ttu-id="bf5f6-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf5f6-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="bf5f6-111">Child Elements</span></span>

<span data-ttu-id="bf5f6-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf5f6-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="bf5f6-113">Parent Elements</span></span>

|<span data-ttu-id="bf5f6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf5f6-114">Element</span></span>|<span data-ttu-id="bf5f6-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="bf5f6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf5f6-116">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bf5f6-117">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bf5f6-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bf5f6-118">Text Value</span></span>

<span data-ttu-id="bf5f6-119">Especifique el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf5f6-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bf5f6-120">Remarks</span></span>

<span data-ttu-id="bf5f6-121">Puede crear controles comunes que se pueden usar en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden usar en una vista específica.</span><span class="sxs-lookup"><span data-stu-id="bf5f6-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="bf5f6-122">Los elementos siguientes especifican los nombres de estos controles:</span><span class="sxs-lookup"><span data-stu-id="bf5f6-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="bf5f6-123">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="bf5f6-124">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="bf5f6-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="bf5f6-125">See Also</span></span>

[<span data-ttu-id="bf5f6-126">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="bf5f6-127">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="bf5f6-128">Elemento ExpressionBinding para CustomItem para GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf5f6-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="bf5f6-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf5f6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
