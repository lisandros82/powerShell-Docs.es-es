---
title: Elemento de bloque de script para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855561"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="fb0cf-102">Elemento ScriptBlock para ListItem for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fb0cf-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="fb0cf-103">Especifica la secuencia de comandos cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="fb0cf-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para ListEntries elemento ListItems de ListControl (formato) para ListEntry elemento ListItem de ListControl (formato) para ListItems de elemento de bloque de script de ListControl (formato) de ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fb0cf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb0cf-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fb0cf-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb0cf-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="fb0cf-106">Attributes and Elements</span></span>

<span data-ttu-id="fb0cf-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb0cf-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb0cf-108">Attributes</span></span>

<span data-ttu-id="fb0cf-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb0cf-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="fb0cf-110">Child Elements</span></span>

<span data-ttu-id="fb0cf-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb0cf-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="fb0cf-112">Parent Elements</span></span>

|<span data-ttu-id="fb0cf-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb0cf-113">Element</span></span>|<span data-ttu-id="fb0cf-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb0cf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb0cf-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="fb0cf-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="fb0cf-116">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fb0cf-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fb0cf-117">Text Value</span></span>

<span data-ttu-id="fb0cf-118">Especifique el script cuyo valor se muestra en la fila.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb0cf-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fb0cf-119">Remarks</span></span>

<span data-ttu-id="fb0cf-120">Cuando se especifica este elemento, no puede especificar el [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="fb0cf-121">Para obtener más información acerca de cómo especificar los scripts en una vista de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fb0cf-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fb0cf-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fb0cf-122">Example</span></span>

<span data-ttu-id="fb0cf-123">El ejemplo siguiente muestra cómo especificar la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="fb0cf-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="fb0cf-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="fb0cf-124">See Also</span></span>

[<span data-ttu-id="fb0cf-125">Elemento PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fb0cf-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="fb0cf-126">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="fb0cf-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fb0cf-127">ListItem (elemento) para ListItems de ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fb0cf-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="fb0cf-128">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb0cf-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)