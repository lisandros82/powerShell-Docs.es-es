---
title: Nombre de elemento de Control para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065111"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="aa91b-102">Elemento Name para Control for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="aa91b-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="aa91b-103">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="aa91b-103">Specifies the name of the control.</span></span>

<span data-ttu-id="aa91b-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento de configuración (formato) controla elemento del Control de elemento (formato) para los controles de vista (formato) nombre del elemento para el Control de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa91b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa91b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aa91b-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa91b-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="aa91b-106">Attributes and Elements</span></span>

<span data-ttu-id="aa91b-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="aa91b-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa91b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="aa91b-108">Attributes</span></span>

<span data-ttu-id="aa91b-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="aa91b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa91b-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="aa91b-110">Child Elements</span></span>

<span data-ttu-id="aa91b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="aa91b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa91b-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="aa91b-112">Parent Elements</span></span>

|<span data-ttu-id="aa91b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa91b-113">Element</span></span>|<span data-ttu-id="aa91b-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="aa91b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa91b-115">Elemento de control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa91b-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="aa91b-116">Define un control que puede usar la vista y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="aa91b-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aa91b-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="aa91b-117">Text Value</span></span>

<span data-ttu-id="aa91b-118">Especifique el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="aa91b-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa91b-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="aa91b-119">Remarks</span></span>

<span data-ttu-id="aa91b-120">El nombre especificado aquí se puede usar en los siguientes elementos para hacer referencia a este control.</span><span class="sxs-lookup"><span data-stu-id="aa91b-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="aa91b-121">Al crear una tabla, lista, vista de control personalizado o amplia, se puede especificar el control con el siguiente elemento: [Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="aa91b-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="aa91b-122">Al crear otro control que se puede usar una vista, este control puede especificarse con el siguiente elemento: [Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="aa91b-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="aa91b-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="aa91b-123">See Also</span></span>

[<span data-ttu-id="aa91b-124">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa91b-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="aa91b-125">Elemento ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa91b-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="aa91b-126">Elemento de control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="aa91b-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="aa91b-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa91b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
