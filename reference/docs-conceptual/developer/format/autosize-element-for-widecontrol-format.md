---
title: AutoSize (elemento) para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369054"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="00e25-102">Elemento AutoSize para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="00e25-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="00e25-103">Especifica si el tamaño de la columna y el número de columnas se ajustan en función del tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="00e25-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="00e25-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) AutoSize para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="00e25-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00e25-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="00e25-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00e25-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="00e25-106">Attributes and Elements</span></span>

<span data-ttu-id="00e25-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `AutoSize`.</span><span class="sxs-lookup"><span data-stu-id="00e25-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00e25-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="00e25-108">Attributes</span></span>

<span data-ttu-id="00e25-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="00e25-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00e25-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="00e25-110">Child Elements</span></span>

<span data-ttu-id="00e25-111">Ninguno</span><span class="sxs-lookup"><span data-stu-id="00e25-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00e25-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="00e25-112">Parent Elements</span></span>

|<span data-ttu-id="00e25-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="00e25-113">Element</span></span>|<span data-ttu-id="00e25-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="00e25-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00e25-115">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="00e25-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="00e25-116">Define un formato de lista ancho (valor único) para la vista.</span><span class="sxs-lookup"><span data-stu-id="00e25-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00e25-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="00e25-117">Remarks</span></span>

<span data-ttu-id="00e25-118">Al definir una vista ampliada, puede Agregar el elemento `AutoSize` o el elemento [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) , pero no puede Agregar ambos.</span><span class="sxs-lookup"><span data-stu-id="00e25-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="00e25-119">Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="00e25-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="00e25-120">Para obtener un ejemplo de una vista amplia, vea [vista ampliada (básica)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="00e25-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00e25-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="00e25-121">See Also</span></span>

[<span data-ttu-id="00e25-122">Elemento ColumnNumber para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="00e25-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="00e25-123">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="00e25-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="00e25-124">Elemento WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="00e25-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="00e25-125">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="00e25-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
