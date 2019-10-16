---
title: Elemento Label de ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362894"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="5b281-102">Elemento Label para ListItem for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="5b281-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="5b281-103">Especifica la etiqueta que se muestra a la izquierda de la propiedad o del valor de script de la fila.</span><span class="sxs-lookup"><span data-stu-id="5b281-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="5b281-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListControl (Format) ListItems para ListEntry para el elemento ListControl ( Format) elemento ListItem para ListItems para el elemento de etiqueta ListControl (Format) para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b281-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b281-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5b281-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b281-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="5b281-106">Attributes and Elements</span></span>

<span data-ttu-id="5b281-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `Label`.</span><span class="sxs-lookup"><span data-stu-id="5b281-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b281-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5b281-108">Attributes</span></span>

<span data-ttu-id="5b281-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5b281-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b281-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="5b281-110">Child Elements</span></span>

<span data-ttu-id="5b281-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5b281-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b281-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="5b281-112">Parent Elements</span></span>

|<span data-ttu-id="5b281-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b281-113">Element</span></span>|<span data-ttu-id="5b281-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="5b281-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b281-115">Elemento ListItem para ListItems para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b281-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5b281-116">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="5b281-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b281-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5b281-117">Text Value</span></span>

<span data-ttu-id="5b281-118">Especifique la etiqueta que se va a mostrar a la izquierda del valor de la propiedad o del script.</span><span class="sxs-lookup"><span data-stu-id="5b281-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b281-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5b281-119">Remarks</span></span>

<span data-ttu-id="5b281-120">Si no se especifica una etiqueta, se muestra el nombre de la propiedad o el script.</span><span class="sxs-lookup"><span data-stu-id="5b281-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="5b281-121">Para obtener más información sobre el uso de etiquetas en una vista de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5b281-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b281-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5b281-122">Example</span></span>

<span data-ttu-id="5b281-123">En el ejemplo siguiente se muestra cómo agregar una etiqueta a una fila.</span><span class="sxs-lookup"><span data-stu-id="5b281-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="5b281-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="5b281-124">See Also</span></span>

[<span data-ttu-id="5b281-125">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="5b281-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5b281-126">ListItem (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="5b281-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5b281-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b281-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
