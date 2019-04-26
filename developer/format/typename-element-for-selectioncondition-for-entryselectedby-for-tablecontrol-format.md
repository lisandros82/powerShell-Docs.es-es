---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083848"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b4505-102">Elemento TypeName para SelectionCondition for EntrySelectedBy for TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b4505-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b4505-103">Especifica un tipo .NET que desencadena la condición.</span><span class="sxs-lookup"><span data-stu-id="b4505-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="b4505-104">Cuando este tipo está presente, se cumple la condición y se utiliza la fila de tabla.</span><span class="sxs-lookup"><span data-stu-id="b4505-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="b4505-105">Elemento (formato) elemento ViewDefinitions (formato) vista elemento (formato) elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuración para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TypeName TableRowEntry (formato) (elemento) para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4505-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4505-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b4505-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4505-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="b4505-107">Attributes and Elements</span></span>

<span data-ttu-id="b4505-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b4505-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4505-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b4505-109">Attributes</span></span>

<span data-ttu-id="b4505-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b4505-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4505-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="b4505-111">Child Elements</span></span>

<span data-ttu-id="b4505-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="b4505-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4505-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="b4505-113">Parent Elements</span></span>

|<span data-ttu-id="b4505-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4505-114">Element</span></span>|<span data-ttu-id="b4505-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="b4505-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4505-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4505-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b4505-117">Define la condición que debe existir para que esta fila de tabla que se usará.</span><span class="sxs-lookup"><span data-stu-id="b4505-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b4505-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b4505-118">Text Value</span></span>

<span data-ttu-id="b4505-119">Especifique el nombre completo del tipo. NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="b4505-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4505-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b4505-120">Remarks</span></span>

<span data-ttu-id="b4505-121">La condición de selección puede especificar cualquier número de tipos de .NET o la selección se establece, pero no puede especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b4505-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="b4505-122">Para obtener más información sobre cómo usar condiciones de selección, consulte [definir condiciones para cuando una entrada de la vista o se usa el elemento](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b4505-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b4505-123">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b4505-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4505-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="b4505-124">See Also</span></span>

[<span data-ttu-id="b4505-125">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="b4505-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b4505-126">Definir condiciones para cuando se muestran los datos</span><span class="sxs-lookup"><span data-stu-id="b4505-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b4505-127">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4505-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b4505-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b4505-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b4505-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4505-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
