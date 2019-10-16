---
title: Elemento Name del control para los controles de configuración (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362714"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="7804c-102">Elemento Name para Control for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="7804c-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7804c-103">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="7804c-103">Specifies the name of the control.</span></span> <span data-ttu-id="7804c-104">Este elemento se utiliza al definir un control común que se puede usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="7804c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7804c-105">Elemento de configuración (formato) elementos del control de configuración (formato) para los controles de configuración (formato) elemento de nombre para el control de los controles para la configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="7804c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7804c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7804c-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7804c-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7804c-107">Attributes and Elements</span></span>

<span data-ttu-id="7804c-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="7804c-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7804c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7804c-109">Attributes</span></span>

<span data-ttu-id="7804c-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7804c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7804c-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7804c-111">Child Elements</span></span>

<span data-ttu-id="7804c-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="7804c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7804c-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7804c-113">Parent Elements</span></span>

|<span data-ttu-id="7804c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7804c-114">Element</span></span>|<span data-ttu-id="7804c-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="7804c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7804c-116">Control (elemento) para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="7804c-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="7804c-117">Define un control común que pueden usar todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="7804c-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7804c-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7804c-118">Text Value</span></span>

<span data-ttu-id="7804c-119">Especifique el nombre que se utiliza para hacer referencia a este control.</span><span class="sxs-lookup"><span data-stu-id="7804c-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="7804c-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7804c-120">Remarks</span></span>

<span data-ttu-id="7804c-121">El nombre especificado aquí se puede usar en los elementos siguientes para hacer referencia a este control.</span><span class="sxs-lookup"><span data-stu-id="7804c-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="7804c-122">Al crear una tabla, lista, vista de control amplia o personalizada, el control puede especificarse mediante el elemento siguiente: [GroupBy (elemento) para View (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="7804c-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="7804c-123">Al crear otro control común, este control se puede especificar mediante el elemento siguiente: [elemento ExpressionBinding de CustomItem para controles de configuración (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="7804c-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="7804c-124">Al crear un control que se puede usar en una vista, este control se puede especificar mediante el elemento siguiente: [ExpressionBinding para CustomItem para los controles de View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="7804c-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="7804c-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="7804c-125">See Also</span></span>

[<span data-ttu-id="7804c-126">Control (elemento) para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="7804c-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="7804c-127">Elemento ExpressionBinding de CustomItem para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="7804c-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7804c-128">Elemento ExpressionBinding para CustomItem para controles para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7804c-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7804c-129">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="7804c-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7804c-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7804c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
