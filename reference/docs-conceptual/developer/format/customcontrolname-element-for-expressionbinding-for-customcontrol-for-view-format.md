---
title: Elemento CustomControlName para ExpressionBinding para CustomControl para View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364114"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="155e9-102">Elemento CustomControlName para ExpressionBinding for CustomControl for View (formato)</span><span class="sxs-lookup"><span data-stu-id="155e9-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="155e9-103">Especifica el nombre de un control común o un control de vista.</span><span class="sxs-lookup"><span data-stu-id="155e9-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="155e9-104">Este elemento se utiliza al definir una vista de control personalizada.</span><span class="sxs-lookup"><span data-stu-id="155e9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="155e9-105">Elemento de configuración (Format) elemento ViewDefinitions (Format) elemento de vista (Format) elemento CustomControl para el elemento de vista (Format) CustomEntries para CustomControl para la vista (Format) elemento CustomEntry para CustomEntries para View (Format) CustomItem Elemento para CustomEntry para el elemento ExpressionBinding de View (Format) para CustomItem (Format) CustomControlName para el enlace de expresiones para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="155e9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="155e9-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="155e9-107">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="155e9-107">Attributes and Elements</span></span>

<span data-ttu-id="155e9-108">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="155e9-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="155e9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="155e9-109">Attributes</span></span>

<span data-ttu-id="155e9-110">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="155e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="155e9-111">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="155e9-111">Child Elements</span></span>

<span data-ttu-id="155e9-112">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="155e9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="155e9-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="155e9-113">Parent Elements</span></span>

|<span data-ttu-id="155e9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="155e9-114">Element</span></span>|<span data-ttu-id="155e9-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="155e9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="155e9-116">Elemento ExpressionBinding para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="155e9-117">Define los datos que muestra el control.</span><span class="sxs-lookup"><span data-stu-id="155e9-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="155e9-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="155e9-118">Text Value</span></span>

<span data-ttu-id="155e9-119">Especifique el nombre del control.</span><span class="sxs-lookup"><span data-stu-id="155e9-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="155e9-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="155e9-120">Remarks</span></span>

<span data-ttu-id="155e9-121">Puede crear controles comunes que se pueden usar en todas las vistas de un archivo de formato y puede crear controles de vista que se pueden usar en una vista específica.</span><span class="sxs-lookup"><span data-stu-id="155e9-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="155e9-122">Los nombres de estos controles se especifican mediante los siguientes elementos.</span><span class="sxs-lookup"><span data-stu-id="155e9-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="155e9-123">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="155e9-124">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="155e9-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="155e9-125">See Also</span></span>

[<span data-ttu-id="155e9-126">Elemento Name del control para los controles de configuración (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="155e9-127">Elemento Name del control para los controles de View (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="155e9-128">Elemento ExpressionBinding para CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="155e9-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="155e9-129">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="155e9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
