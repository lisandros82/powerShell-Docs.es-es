---
title: Elemento CustomControlName para GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368884"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="d68f0-102">Elemento CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d68f0-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="d68f0-103">Especifica el nombre de un control personalizado que se usa para mostrar el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="d68f0-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="d68f0-104">Este elemento se utiliza al definir una vista de control de tabla, lista, ancho o personalizado.</span><span class="sxs-lookup"><span data-stu-id="d68f0-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="d68f0-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento GroupBy para el elemento View (Format) CustomControlName de GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d68f0-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d68f0-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d68f0-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="d68f0-107">Attributes and Elements</span></span>

<span data-ttu-id="d68f0-108">En las secciones siguientes se describen los atributos, los elementos secundarios y los elementos primarios del elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="d68f0-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d68f0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d68f0-109">Attributes</span></span>

<span data-ttu-id="d68f0-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d68f0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d68f0-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="d68f0-111">Child Elements</span></span>

<span data-ttu-id="d68f0-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="d68f0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d68f0-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="d68f0-113">Parent Elements</span></span>

|<span data-ttu-id="d68f0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="d68f0-114">Element</span></span>|<span data-ttu-id="d68f0-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="d68f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d68f0-116">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="d68f0-117">Define cómo Windows PowerShell muestra un nuevo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="d68f0-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d68f0-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d68f0-118">Text Value</span></span>

<span data-ttu-id="d68f0-119">Especifique el nombre del control personalizado que se usa para mostrar un nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="d68f0-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="d68f0-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d68f0-120">Remarks</span></span>

<span data-ttu-id="d68f0-121">Puede crear controles comunes que se pueden usar en todas las vistas de un archivo de formato, y puede crear controles de vista que se pueden usar en una vista específica.</span><span class="sxs-lookup"><span data-stu-id="d68f0-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="d68f0-122">Los elementos siguientes especifican los nombres de estos controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="d68f0-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="d68f0-123">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d68f0-124">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d68f0-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="d68f0-125">See Also</span></span>

[<span data-ttu-id="d68f0-126">Elemento GroupBy para View (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d68f0-127">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d68f0-128">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="d68f0-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d68f0-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d68f0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
