---
title: Elemento ScriptBlock para WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362034"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="2dded-102">Elemento ScriptBlock para WideItem for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="2dded-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="2dded-103">Especifica el script cuyo valor se muestra en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="2dded-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="2dded-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry (Format) elemento WideItem (Format) elemento ScriptBlock para WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2dded-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2dded-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2dded-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2dded-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="2dded-106">Attributes and Elements</span></span>

<span data-ttu-id="2dded-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="2dded-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2dded-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="2dded-108">Attributes</span></span>

<span data-ttu-id="2dded-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2dded-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2dded-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2dded-110">Child Elements</span></span>

<span data-ttu-id="2dded-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="2dded-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2dded-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="2dded-112">Parent Elements</span></span>

|<span data-ttu-id="2dded-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2dded-113">Element</span></span>|<span data-ttu-id="2dded-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dded-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2dded-115">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2dded-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="2dded-116">Define la propiedad o el bloque de script cuyo valor se muestra en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="2dded-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2dded-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="2dded-117">Text Value</span></span>

<span data-ttu-id="2dded-118">Especifique el script cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="2dded-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2dded-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2dded-119">Remarks</span></span>

<span data-ttu-id="2dded-120">Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2dded-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2dded-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dded-121">Example</span></span>

<span data-ttu-id="2dded-122">En este ejemplo se muestra un elemento `WideItem` que define un script cuyo valor se muestra en la vista.</span><span class="sxs-lookup"><span data-stu-id="2dded-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="2dded-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="2dded-123">See Also</span></span>

[<span data-ttu-id="2dded-124">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2dded-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="2dded-125">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="2dded-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2dded-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dded-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
