---
title: Elemento CustomControlName para ExpressionBinding para los controles de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066641"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="9ff7f-102">Elemento CustomControlName para ExpressionBinding for Controls for Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9ff7f-103">Especifica el nombre de un control común.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-103">Specifies the name of a common control.</span></span> <span data-ttu-id="9ff7f-104">Este elemento se usa al definir un control común que puede usarse en todas las vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9ff7f-105">Elemento de configuración (formato) elemento controles de elemento de Control de configuración (formato) para los controles de elemento de control personalizado de configuración (formato) para el Control de elemento de configuración (formato) CustomEntries para el control personalizado para la configuración ( Elemento de CustomEntry Format) para el control personalizado para los controles de elemento de configuración (formato) CustomItem para CustomEntry para los controles de elemento de configuración ExpressionBinding CustomItem para los controles de configuración (formato) CustomControlName Elemento para ExpressionBinding para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ff7f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9ff7f-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ff7f-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9ff7f-107">Attributes and Elements</span></span>

<span data-ttu-id="9ff7f-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ff7f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ff7f-109">Attributes</span></span>

<span data-ttu-id="9ff7f-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ff7f-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9ff7f-111">Child Elements</span></span>

<span data-ttu-id="9ff7f-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9ff7f-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9ff7f-113">Parent Elements</span></span>

|<span data-ttu-id="9ff7f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9ff7f-114">Element</span></span>|<span data-ttu-id="9ff7f-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="9ff7f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ff7f-116">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="9ff7f-117">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9ff7f-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9ff7f-118">Text Value</span></span>

<span data-ttu-id="9ff7f-119">Especifique el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ff7f-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9ff7f-120">Remarks</span></span>

<span data-ttu-id="9ff7f-121">Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden utilizar una vista específica.</span><span class="sxs-lookup"><span data-stu-id="9ff7f-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="9ff7f-122">Los siguientes elementos especifican los nombres de estos controles:</span><span class="sxs-lookup"><span data-stu-id="9ff7f-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="9ff7f-123">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="9ff7f-124">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="9ff7f-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="9ff7f-125">See Also</span></span>

[<span data-ttu-id="9ff7f-126">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9ff7f-127">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="9ff7f-128">Elemento ExpressionBinding para CustomItem para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="9ff7f-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="9ff7f-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ff7f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
