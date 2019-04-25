---
title: Elemento FormatString para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065631"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="9a4a6-102">Elemento FormatString para ListItem for ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="9a4a6-103">Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="9a4a6-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento ListControl (formato) ListEntries elemento de configuración (elemento) ListEntry ListControl (formato) para el elemento ListItems de ListControl (formato) de ListControl (formato) Elemento ListItem, por elemento FormatString de ListControl (formato) para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a4a6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9a4a6-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a4a6-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="9a4a6-106">Attributes and Elements</span></span>

<span data-ttu-id="9a4a6-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a4a6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a4a6-108">Attributes</span></span>

<span data-ttu-id="9a4a6-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a4a6-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="9a4a6-110">Child Elements</span></span>

<span data-ttu-id="9a4a6-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a4a6-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="9a4a6-112">Parent Elements</span></span>

|<span data-ttu-id="9a4a6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a4a6-113">Element</span></span>|<span data-ttu-id="9a4a6-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="9a4a6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a4a6-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="9a4a6-116">Define la propiedad o el script cuyo valor se muestra en una fila de la vista de lista.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a4a6-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9a4a6-117">Text Value</span></span>

<span data-ttu-id="9a4a6-118">Especifique el patrón que se usa para dar formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="9a4a6-119">Por ejemplo, puede usar este patrón para dar formato al valor de cualquier propiedad que es del tipo [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a4a6-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9a4a6-120">Remarks</span></span>

<span data-ttu-id="9a4a6-121">Cadenas de formato pueden usarse al crear las vistas de tablas, vistas de lista, vista amplia o vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="9a4a6-122">Para obtener más información sobre cómo dar formato a un valor que se muestran en una vista, consulte [dar formato a datos de muestra](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="9a4a6-123">Para obtener más información sobre cómo usar cadenas de formato en las vistas de lista, consulte [Crear vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a4a6-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9a4a6-124">Example</span></span>

<span data-ttu-id="9a4a6-125">El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="9a4a6-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="9a4a6-126">See Also</span></span>

[<span data-ttu-id="9a4a6-127">Creación de una vista de lista</span><span class="sxs-lookup"><span data-stu-id="9a4a6-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9a4a6-128">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="9a4a6-129">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="9a4a6-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
