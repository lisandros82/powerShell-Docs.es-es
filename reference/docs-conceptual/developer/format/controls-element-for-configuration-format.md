---
title: Elemento Controls para Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369004"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="3efdf-102">Elemento Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="3efdf-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="3efdf-103">Define los controles comunes que se pueden usar en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="3efdf-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="3efdf-104">Elemento Configuration (Format) Controls de la configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="3efdf-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3efdf-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3efdf-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3efdf-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="3efdf-106">Attributes and Elements</span></span>

<span data-ttu-id="3efdf-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Controls`.</span><span class="sxs-lookup"><span data-stu-id="3efdf-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3efdf-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3efdf-108">Attributes</span></span>

<span data-ttu-id="3efdf-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="3efdf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3efdf-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="3efdf-110">Child Elements</span></span>

|<span data-ttu-id="3efdf-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="3efdf-111">Element</span></span>|<span data-ttu-id="3efdf-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="3efdf-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3efdf-113">Control (elemento) para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="3efdf-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="3efdf-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="3efdf-114">Required element.</span></span><br /><br /> <span data-ttu-id="3efdf-115">Define un control común que pueden usar todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="3efdf-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3efdf-116">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="3efdf-116">Parent Elements</span></span>

|<span data-ttu-id="3efdf-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="3efdf-117">Element</span></span>|<span data-ttu-id="3efdf-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="3efdf-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3efdf-119">Configuration (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="3efdf-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="3efdf-120">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="3efdf-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3efdf-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3efdf-121">Remarks</span></span>

<span data-ttu-id="3efdf-122">Puede crear cualquier número de controles comunes.</span><span class="sxs-lookup"><span data-stu-id="3efdf-122">You can create any number of common controls.</span></span> <span data-ttu-id="3efdf-123">Para cada control, debe especificar el nombre que se utiliza para hacer referencia al control y los componentes del control.</span><span class="sxs-lookup"><span data-stu-id="3efdf-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="3efdf-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="3efdf-124">See Also</span></span>

[<span data-ttu-id="3efdf-125">Configuration (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="3efdf-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="3efdf-126">Control (elemento) para controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="3efdf-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="3efdf-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3efdf-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
