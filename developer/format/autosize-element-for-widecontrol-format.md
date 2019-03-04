---
title: Elemento AutoSize para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857091"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="dd429-102">Elemento AutoSize para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dd429-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="dd429-103">Especifica si el tamaño de columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="dd429-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="dd429-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) Autosize elemento de configuración WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dd429-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd429-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dd429-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd429-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="dd429-106">Attributes and Elements</span></span>

<span data-ttu-id="dd429-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `AutoSize` elemento.</span><span class="sxs-lookup"><span data-stu-id="dd429-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd429-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd429-108">Attributes</span></span>

<span data-ttu-id="dd429-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="dd429-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd429-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="dd429-110">Child Elements</span></span>

<span data-ttu-id="dd429-111">Ninguno</span><span class="sxs-lookup"><span data-stu-id="dd429-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd429-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="dd429-112">Parent Elements</span></span>

|<span data-ttu-id="dd429-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd429-113">Element</span></span>|<span data-ttu-id="dd429-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="dd429-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd429-115">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dd429-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="dd429-116">Define una amplia (valor single) formato de lista para la vista.</span><span class="sxs-lookup"><span data-stu-id="dd429-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd429-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="dd429-117">Remarks</span></span>

<span data-ttu-id="dd429-118">Al definir una vista amplia, puede agregar el `AutoSize` elemento o el [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento, pero no se puede agregar ambos.</span><span class="sxs-lookup"><span data-stu-id="dd429-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="dd429-119">Para obtener más información acerca de los componentes de una vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="dd429-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="dd429-120">Para obtener un ejemplo de una vista amplia, consulte [vista amplia (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="dd429-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd429-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="dd429-121">See Also</span></span>

[<span data-ttu-id="dd429-122">Elemento ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dd429-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="dd429-123">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="dd429-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dd429-124">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dd429-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="dd429-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd429-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
