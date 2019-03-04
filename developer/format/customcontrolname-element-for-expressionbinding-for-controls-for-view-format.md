---
title: Elemento CustomControlName para ExpressionBinding para los controles de vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855601"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="f7e2f-102">Elemento CustomControlName para ExpressionBinding for Controls for View (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="f7e2f-103">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="f7e2f-104">Este elemento se usa al definir los controles que pueden usarse en una vista.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f7e2f-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) controles (formato) del elemento Control elemento de configuración para los controles de elemento de control personalizado (formato) de la vista de Control para los controles de elemento de vista (formato) CustomEntries para Control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para los controles de elemento de vista (formato) CustomItem para CustomEntry para los controles de elemento de vista (formato) ExpressionBinding para CustomItem para los controles de vista (formato) CustomControlName Elemento para ExpressionBindine para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7e2f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f7e2f-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7e2f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="f7e2f-107">Attributes and Elements</span></span>

<span data-ttu-id="f7e2f-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7e2f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7e2f-109">Attributes</span></span>

<span data-ttu-id="f7e2f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7e2f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="f7e2f-111">Child Elements</span></span>

<span data-ttu-id="f7e2f-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f7e2f-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="f7e2f-113">Parent Elements</span></span>

|<span data-ttu-id="f7e2f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7e2f-114">Element</span></span>|<span data-ttu-id="f7e2f-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="f7e2f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7e2f-116">Elemento ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f7e2f-117">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f7e2f-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f7e2f-118">Text Value</span></span>

<span data-ttu-id="f7e2f-119">Especifique el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7e2f-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f7e2f-120">Remarks</span></span>

<span data-ttu-id="f7e2f-121">Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden utilizar una vista específica.</span><span class="sxs-lookup"><span data-stu-id="f7e2f-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="f7e2f-122">Los siguientes elementos especifican los nombres de estos controles:</span><span class="sxs-lookup"><span data-stu-id="f7e2f-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="f7e2f-123">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="f7e2f-124">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="f7e2f-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="f7e2f-125">See Also</span></span>

[<span data-ttu-id="f7e2f-126">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7e2f-127">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f7e2f-128">Elemento ExpressionBinding para CustomItem para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="f7e2f-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f7e2f-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7e2f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
