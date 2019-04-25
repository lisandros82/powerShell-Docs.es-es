---
title: Elemento PropertyName para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064924"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e992b-102">Elemento PropertyName para ListItem for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e992b-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e992b-103">Especifica la propiedad de .NET cuyo valor se muestra en la lista.</span><span class="sxs-lookup"><span data-stu-id="e992b-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="e992b-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) elemento ListItems (formato) elemento ListItem (formato) PropertyName elemento de configuración para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e992b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e992b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e992b-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e992b-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e992b-106">Attributes and Elements</span></span>

<span data-ttu-id="e992b-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e992b-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e992b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e992b-108">Attributes</span></span>

<span data-ttu-id="e992b-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e992b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e992b-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e992b-110">Child Elements</span></span>

<span data-ttu-id="e992b-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e992b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e992b-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e992b-112">Parent Elements</span></span>

|<span data-ttu-id="e992b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e992b-113">Element</span></span>|<span data-ttu-id="e992b-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="e992b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e992b-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e992b-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e992b-116">Define la propiedad o el script cuyo valor se muestra en la fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="e992b-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e992b-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e992b-117">Text Value</span></span>

<span data-ttu-id="e992b-118">Especifique el nombre de la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="e992b-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e992b-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e992b-119">Remarks</span></span>

<span data-ttu-id="e992b-120">Cuando se especifica este elemento, no puede especificar el [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="e992b-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="e992b-121">Además de mostrar el valor de propiedad, también puede especificar una etiqueta para el valor o una cadena de formato que puede utilizarse para cambiar la presentación del valor.</span><span class="sxs-lookup"><span data-stu-id="e992b-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="e992b-122">Para obtener más información acerca de cómo especificar los datos en una vista de lista, consulte [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e992b-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e992b-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e992b-123">Example</span></span>

<span data-ttu-id="e992b-124">El ejemplo siguiente muestra cómo especificar la etiqueta y la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="e992b-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="e992b-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="e992b-125">See Also</span></span>

[<span data-ttu-id="e992b-126">Elemento de bloque de script para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e992b-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e992b-127">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="e992b-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e992b-128">ListItem (elemento) para ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="e992b-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e992b-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e992b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
