---
title: Elemento FormatString para ListItem para ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363024"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="5d491-102">Elemento FormatString para ListItem for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="5d491-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="5d491-103">Especifica un modelo de formato que define cómo se muestra el valor de la propiedad o del script.</span><span class="sxs-lookup"><span data-stu-id="5d491-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="5d491-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento ListControl (Format) elemento ListEntries para ListControl (Format) elemento ListEntry para ListControl (Format) elemento ListItems para ListControl (Format) Elemento ListItem para ListControl (Format) elemento FormatString para ListItem para ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5d491-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d491-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5d491-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d491-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="5d491-106">Attributes and Elements</span></span>

<span data-ttu-id="5d491-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="5d491-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d491-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d491-108">Attributes</span></span>

<span data-ttu-id="5d491-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5d491-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d491-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="5d491-110">Child Elements</span></span>

<span data-ttu-id="5d491-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="5d491-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d491-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="5d491-112">Parent Elements</span></span>

|<span data-ttu-id="5d491-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d491-113">Element</span></span>|<span data-ttu-id="5d491-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d491-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d491-115">ListItem (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="5d491-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5d491-116">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="5d491-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5d491-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5d491-117">Text Value</span></span>

<span data-ttu-id="5d491-118">Especifique el patrón que se utiliza para dar formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="5d491-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="5d491-119">Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que sea del tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: HH}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="5d491-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d491-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5d491-120">Remarks</span></span>

<span data-ttu-id="5d491-121">Las cadenas de formato se pueden usar al crear vistas de tabla, vistas de lista, vistas anchas o vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5d491-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="5d491-122">Para obtener más información sobre cómo dar formato a un valor que se muestra en una vista, vea [aplicar formato a los datos mostrados](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="5d491-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="5d491-123">Para obtener más información sobre el uso de cadenas de formato en las vistas de lista, vea [crear una vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5d491-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d491-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d491-124">Example</span></span>

<span data-ttu-id="5d491-125">En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="5d491-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="5d491-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="5d491-126">See Also</span></span>

[<span data-ttu-id="5d491-127">Crear una vista de lista</span><span class="sxs-lookup"><span data-stu-id="5d491-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5d491-128">ListItem (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="5d491-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5d491-129">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d491-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
