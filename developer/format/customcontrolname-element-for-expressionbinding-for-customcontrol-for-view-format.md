---
title: Elemento CustomControlName para ExpressionBinding para el control personalizado para la vista (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860441"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="111d9-102">Elemento CustomControlName para ExpressionBinding for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="111d9-103">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="111d9-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="111d9-104">Este elemento se usa al definir una vista de control personalizado.</span><span class="sxs-lookup"><span data-stu-id="111d9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="111d9-105">Configuración (formato) elemento ViewDefinitions (formato) Vista (formato) del elemento control personalizado elemento de vista (formato) del elemento CustomEntries para el control personalizado de vista (formato) del elemento CustomEntry para CustomEntries para CustomItem vista (formato) Elemento para CustomEntry de vista (formato) del elemento ExpressionBinding CustomItem (formato) CustomControlName elemento de enlace de expresiones para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="111d9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="111d9-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="111d9-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="111d9-107">Attributes and Elements</span></span>

<span data-ttu-id="111d9-108">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="111d9-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="111d9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="111d9-109">Attributes</span></span>

<span data-ttu-id="111d9-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="111d9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="111d9-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="111d9-111">Child Elements</span></span>

<span data-ttu-id="111d9-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="111d9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="111d9-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="111d9-113">Parent Elements</span></span>

|<span data-ttu-id="111d9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="111d9-114">Element</span></span>|<span data-ttu-id="111d9-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="111d9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="111d9-116">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="111d9-117">Define los datos que se muestran el control.</span><span class="sxs-lookup"><span data-stu-id="111d9-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="111d9-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="111d9-118">Text Value</span></span>

<span data-ttu-id="111d9-119">Especifique el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="111d9-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="111d9-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="111d9-120">Remarks</span></span>

<span data-ttu-id="111d9-121">Puede crear controles comunes que pueden usarse en todas las vistas de un archivo de formato y puede crear controles de vista que se pueden utilizar una vista específica.</span><span class="sxs-lookup"><span data-stu-id="111d9-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="111d9-122">Los nombres de estos controles se especifican mediante los siguientes elementos.</span><span class="sxs-lookup"><span data-stu-id="111d9-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="111d9-123">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="111d9-124">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="111d9-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="111d9-125">See Also</span></span>

[<span data-ttu-id="111d9-126">Elemento Name de Control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="111d9-127">Elemento Name de Control para los controles de vista (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="111d9-128">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="111d9-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="111d9-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="111d9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)