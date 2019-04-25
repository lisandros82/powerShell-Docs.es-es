---
title: Nombre de elemento de Control para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065196"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="f4fcb-102">Elemento Name para Control for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f4fcb-103">Especifica el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-103">Specifies the name of the control.</span></span> <span data-ttu-id="f4fcb-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f4fcb-105">Elemento de configuración elemento (formato de) los controles de elemento de Control de configuración (formato) para los controles de elemento de nombre de configuración (formato) para el Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4fcb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f4fcb-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4fcb-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f4fcb-107">Attributes and Elements</span></span>

<span data-ttu-id="f4fcb-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4fcb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4fcb-109">Attributes</span></span>

<span data-ttu-id="f4fcb-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4fcb-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f4fcb-111">Child Elements</span></span>

<span data-ttu-id="f4fcb-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4fcb-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f4fcb-113">Parent Elements</span></span>

|<span data-ttu-id="f4fcb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4fcb-114">Element</span></span>|<span data-ttu-id="f4fcb-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="f4fcb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4fcb-116">Elemento de control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="f4fcb-117">Define un control común que puede usarse en todas las vistas del archivo de formato y el nombre que se usa para hacer referencia al control.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4fcb-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f4fcb-118">Text Value</span></span>

<span data-ttu-id="f4fcb-119">Especifique el nombre que se usa para hacer referencia a este control.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4fcb-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f4fcb-120">Remarks</span></span>

<span data-ttu-id="f4fcb-121">El nombre especificado aquí se puede usar en los siguientes elementos para hacer referencia a este control.</span><span class="sxs-lookup"><span data-stu-id="f4fcb-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="f4fcb-122">Al crear una tabla, lista, vista de control personalizado o amplia, se puede especificar el control con el siguiente elemento: [Elemento GroupBy para vista (formato)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="f4fcb-123">Cuando se crea otro control comunes, este control se puede especificar con el siguiente elemento: [Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="f4fcb-124">Al crear un control que se puede usar una vista, este control puede especificarse con el siguiente elemento: [Elemento ExpressionBinding para CustomItem para los controles de vista (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="f4fcb-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="f4fcb-125">See Also</span></span>

[<span data-ttu-id="f4fcb-126">Elemento de control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4fcb-127">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4fcb-128">Elemento ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f4fcb-129">Elemento GroupBy para vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f4fcb-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="f4fcb-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4fcb-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
