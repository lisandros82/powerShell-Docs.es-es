---
title: Elemento PropertyName para WideItem para WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364944"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="b44b7-102">Elemento PropertyName para WideItem for WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b44b7-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="b44b7-103">Especifica la propiedad del objeto cuyo valor se muestra en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="b44b7-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="b44b7-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b44b7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b44b7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b44b7-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b44b7-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b44b7-106">Attributes and Elements</span></span>

<span data-ttu-id="b44b7-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="b44b7-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b44b7-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b44b7-108">Attributes</span></span>

<span data-ttu-id="b44b7-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b44b7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b44b7-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b44b7-110">Child Elements</span></span>

<span data-ttu-id="b44b7-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b44b7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b44b7-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b44b7-112">Parent Elements</span></span>

|<span data-ttu-id="b44b7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b44b7-113">Element</span></span>|<span data-ttu-id="b44b7-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="b44b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b44b7-115">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b44b7-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="b44b7-116">Define la propiedad o el script cuyo valor se muestra en la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="b44b7-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b44b7-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b44b7-117">Text Value</span></span>

<span data-ttu-id="b44b7-118">Especifique el nombre de la propiedad cuyo valor se muestra.</span><span class="sxs-lookup"><span data-stu-id="b44b7-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b44b7-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b44b7-119">Remarks</span></span>

<span data-ttu-id="b44b7-120">Para obtener más información sobre los componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b44b7-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b44b7-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b44b7-121">Example</span></span>

<span data-ttu-id="b44b7-122">En este ejemplo se muestra una vista amplia que muestra el valor de la propiedad processName del objeto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="b44b7-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="b44b7-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="b44b7-123">See Also</span></span>

[<span data-ttu-id="b44b7-124">Elemento WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b44b7-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="b44b7-125">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="b44b7-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b44b7-126">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b44b7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
