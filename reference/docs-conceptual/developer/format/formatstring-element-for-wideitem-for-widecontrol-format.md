---
title: Elemento FormatString para WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363034"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="331a8-102">Elemento FormatString para WideItem for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="331a8-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="331a8-103">Especifica un modelo de formato que define cómo se muestra la propiedad o el valor de script en la vista.</span><span class="sxs-lookup"><span data-stu-id="331a8-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="331a8-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) elemento WideEntry para WideControl (Format) WideItem Element for WideControl (Format) elemento FormatString para WideItem para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="331a8-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="331a8-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="331a8-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="331a8-106">Attributes and Elements</span></span>

<span data-ttu-id="331a8-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="331a8-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="331a8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="331a8-108">Attributes</span></span>

<span data-ttu-id="331a8-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="331a8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="331a8-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="331a8-110">Child Elements</span></span>

<span data-ttu-id="331a8-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="331a8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="331a8-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="331a8-112">Parent Elements</span></span>

|<span data-ttu-id="331a8-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="331a8-113">Element</span></span>|<span data-ttu-id="331a8-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="331a8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="331a8-115">Elemento WideItem para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="331a8-116">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="331a8-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="331a8-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="331a8-117">Text Value</span></span>

<span data-ttu-id="331a8-118">Especifique el patrón que se utiliza para dar formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="331a8-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="331a8-119">Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que sea del tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: HH}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="331a8-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="331a8-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="331a8-120">Remarks</span></span>

<span data-ttu-id="331a8-121">Las cadenas de formato se pueden usar al crear vistas de tabla, vistas de lista, vistas anchas o vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="331a8-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="331a8-122">Para obtener más información sobre cómo dar formato a un valor que se muestra en una vista, vea [aplicar formato a los datos mostrados](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="331a8-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="331a8-123">Para obtener más información sobre el uso de cadenas de formato en las vistas anchas, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="331a8-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="331a8-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="331a8-124">Example</span></span>

<span data-ttu-id="331a8-125">En el ejemplo siguiente se muestra cómo definir una cadena de formato para el valor de la propiedad `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="331a8-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="331a8-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="331a8-126">See Also</span></span>

[<span data-ttu-id="331a8-127">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="331a8-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="331a8-128">Elemento WideItem para WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="331a8-129">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="331a8-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
