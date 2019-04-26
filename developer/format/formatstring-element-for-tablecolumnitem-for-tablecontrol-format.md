---
title: Elemento FormatString para TableColumnItem para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065644"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="880ad-102">Elemento FormatString para TableColumnItem for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="880ad-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="880ad-103">Especifica un patrón de formato que define cómo se muestra el valor de propiedad o un script de la tabla.</span><span class="sxs-lookup"><span data-stu-id="880ad-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="880ad-104">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento de configuración (formato) Elemento FormatString para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="880ad-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="880ad-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="880ad-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="880ad-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="880ad-106">Attributes and Elements</span></span>

<span data-ttu-id="880ad-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="880ad-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="880ad-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="880ad-108">Attributes</span></span>

<span data-ttu-id="880ad-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="880ad-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="880ad-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="880ad-110">Child Elements</span></span>

<span data-ttu-id="880ad-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="880ad-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="880ad-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="880ad-112">Parent Elements</span></span>

|<span data-ttu-id="880ad-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="880ad-113">Element</span></span>|<span data-ttu-id="880ad-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="880ad-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="880ad-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="880ad-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="880ad-116">Define la propiedad o el script cuyo valor se muestra en la columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="880ad-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="880ad-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="880ad-117">Text Value</span></span>

<span data-ttu-id="880ad-118">Especifique el patrón que se usa para dar formato a los datos.</span><span class="sxs-lookup"><span data-stu-id="880ad-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="880ad-119">Por ejemplo, este patrón se puede usar para dar formato al valor de cualquier propiedad que es del tipo [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="880ad-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="880ad-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="880ad-120">Remarks</span></span>

<span data-ttu-id="880ad-121">Cadenas de formato pueden usarse al crear las vistas de tablas, vistas de lista, vista amplia o vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="880ad-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="880ad-122">Para obtener más información sobre cómo dar formato a un valor que se muestran en una vista, consulte [dar formato a datos de muestra](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="880ad-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="880ad-123">Para obtener más información acerca de los componentes de una vista de tabla, vea [vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="880ad-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="880ad-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="880ad-124">Example</span></span>

<span data-ttu-id="880ad-125">El ejemplo siguiente muestra cómo definir una cadena de formato para el valor de la `StartTime` propiedad.</span><span class="sxs-lookup"><span data-stu-id="880ad-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="880ad-126">Véase también</span><span class="sxs-lookup"><span data-stu-id="880ad-126">See Also</span></span>

[<span data-ttu-id="880ad-127">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="880ad-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="880ad-128">Aplicar formato a los datos mostrados</span><span class="sxs-lookup"><span data-stu-id="880ad-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="880ad-129">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="880ad-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="880ad-130">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="880ad-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
