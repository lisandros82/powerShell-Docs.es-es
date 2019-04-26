---
title: Elemento CustomControlName para ExpressionBinding para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066579"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="8b5cc-102">Elemento CustomControlName para ExpressionBinding for GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="8b5cc-103">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="8b5cc-104">Este elemento se usa al definir cómo se muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8b5cc-105">Configuración (formato) elemento ViewDefinitions (formato) vista elemento (formato) GroupBy elemento de elemento de control personalizado (formato) de la vista de elemento de CustomEntries GroupBy (formato) para el control personalizado de elemento de CustomEntry GroupBy (formato) para Control personalizado para GroupBy (formato) (elemento) CustomItem para CustomEntry para GroupBy (formato) (elemento) ExpressionBinding para CustomItem para GroupBy (formato) (elemento) CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b5cc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8b5cc-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b5cc-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="8b5cc-107">Attributes and Elements</span></span>

<span data-ttu-id="8b5cc-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b5cc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b5cc-109">Attributes</span></span>

<span data-ttu-id="8b5cc-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b5cc-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="8b5cc-111">Child Elements</span></span>

<span data-ttu-id="8b5cc-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b5cc-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="8b5cc-113">Parent Elements</span></span>

|<span data-ttu-id="8b5cc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b5cc-114">Element</span></span>|<span data-ttu-id="8b5cc-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b5cc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b5cc-116">Elemento ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="8b5cc-117">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b5cc-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8b5cc-118">Text Value</span></span>

<span data-ttu-id="8b5cc-119">Especifique el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b5cc-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8b5cc-120">Remarks</span></span>

<span data-ttu-id="8b5cc-121">Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden utilizar una vista específica.</span><span class="sxs-lookup"><span data-stu-id="8b5cc-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="8b5cc-122">Los siguientes elementos especifican los nombres de estos controles:</span><span class="sxs-lookup"><span data-stu-id="8b5cc-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="8b5cc-123">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="8b5cc-124">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="8b5cc-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="8b5cc-125">See Also</span></span>

[<span data-ttu-id="8b5cc-126">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8b5cc-127">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="8b5cc-128">Elemento ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8b5cc-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="8b5cc-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b5cc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
