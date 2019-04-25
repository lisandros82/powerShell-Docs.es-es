---
title: Elemento FormatString para WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065689"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="802b0-102">Elemento FormatString para WideItem for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="802b0-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="802b0-103">Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script en la vista.</span><span class="sxs-lookup"><span data-stu-id="802b0-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="802b0-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento de configuración (elemento) WideItem WideControl (formato) para el elemento FormatString de WideControl (formato) para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="802b0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="802b0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="802b0-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="802b0-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="802b0-106">Attributes and Elements</span></span>

<span data-ttu-id="802b0-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="802b0-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="802b0-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="802b0-108">Attributes</span></span>

<span data-ttu-id="802b0-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="802b0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="802b0-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="802b0-110">Child Elements</span></span>

<span data-ttu-id="802b0-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="802b0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="802b0-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="802b0-112">Parent Elements</span></span>

|<span data-ttu-id="802b0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="802b0-113">Element</span></span>|<span data-ttu-id="802b0-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="802b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="802b0-115">Elemento WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="802b0-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="802b0-116">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="802b0-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="802b0-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="802b0-117">Text Value</span></span>

<span data-ttu-id="802b0-118">Especifique el patrón que se usa para dar formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="802b0-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="802b0-119">Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que es del tipo [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="802b0-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="802b0-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="802b0-120">Remarks</span></span>

<span data-ttu-id="802b0-121">Cadenas de formato pueden usarse al crear las vistas de tablas, vistas de lista, vista amplia o vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="802b0-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="802b0-122">Para obtener más información sobre cómo dar formato a un valor que se muestran en una vista, consulte [dar formato a datos de muestra](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="802b0-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="802b0-123">Para obtener más información sobre cómo usar cadenas de formato en vista amplia, consulte [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="802b0-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="802b0-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="802b0-124">Example</span></span>

<span data-ttu-id="802b0-125">El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.</span><span class="sxs-lookup"><span data-stu-id="802b0-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="802b0-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="802b0-126">See Also</span></span>

[<span data-ttu-id="802b0-127">Creación de una vista amplia</span><span class="sxs-lookup"><span data-stu-id="802b0-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="802b0-128">Elemento WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="802b0-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="802b0-129">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="802b0-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
