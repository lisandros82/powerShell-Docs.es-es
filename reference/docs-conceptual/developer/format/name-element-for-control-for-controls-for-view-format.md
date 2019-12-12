---
title: Elemento Name del control para los controles de la vista (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365104"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="c3dc3-102">Elemento Name para Control for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="c3dc3-103">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-103">Specifies the name of the control.</span></span>

<span data-ttu-id="c3dc3-104">Elemento Configuration (Format) elemento ViewDefinitions (formato) elemento de vista (Format) elemento Controls (Format) elemento control para controles para el elemento Name de View (Format) para control para View (Format)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3dc3-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c3dc3-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3dc3-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="c3dc3-106">Attributes and Elements</span></span>

<span data-ttu-id="c3dc3-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3dc3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3dc3-108">Attributes</span></span>

<span data-ttu-id="c3dc3-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3dc3-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="c3dc3-110">Child Elements</span></span>

<span data-ttu-id="c3dc3-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3dc3-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="c3dc3-112">Parent Elements</span></span>

|<span data-ttu-id="c3dc3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3dc3-113">Element</span></span>|<span data-ttu-id="c3dc3-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="c3dc3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3dc3-115">Control (elemento) para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="c3dc3-116">Define un control que se puede usar en la vista y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3dc3-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="c3dc3-117">Text Value</span></span>

<span data-ttu-id="c3dc3-118">Especifique el nombre que se utiliza para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3dc3-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c3dc3-119">Remarks</span></span>

<span data-ttu-id="c3dc3-120">El nombre especificado aquí se puede usar en los elementos siguientes para hacer referencia a este control.</span><span class="sxs-lookup"><span data-stu-id="c3dc3-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="c3dc3-121">Al crear una tabla, lista, vista de control amplia o personalizada, el control puede especificarse mediante el elemento siguiente: [GroupBy (elemento) para View (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="c3dc3-122">Al crear otro control que puede ser utilizado por una vista, este control se puede especificar mediante el elemento siguiente: [ExpressionBinding para CustomItem para los controles de View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c3dc3-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="c3dc3-123">See Also</span></span>

[<span data-ttu-id="c3dc3-124">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c3dc3-125">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c3dc3-126">Control (elemento) para controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="c3dc3-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="c3dc3-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3dc3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
