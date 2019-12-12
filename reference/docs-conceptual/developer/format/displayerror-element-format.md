---
title: Elemento DisplayError (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363994"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="e1c65-102">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="e1c65-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="e1c65-103">Especifica que el #ERR de cadena se muestra cuando se produce un error que muestra un fragmento de datos.</span><span class="sxs-lookup"><span data-stu-id="e1c65-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="e1c65-104">Elemento Configuration (Format) elemento DefaultSettings (Format) elemento DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c65-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1c65-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e1c65-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1c65-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e1c65-106">Attributes and Elements</span></span>

<span data-ttu-id="e1c65-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `DisplayError`.</span><span class="sxs-lookup"><span data-stu-id="e1c65-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1c65-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1c65-108">Attributes</span></span>

<span data-ttu-id="e1c65-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1c65-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1c65-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e1c65-110">Child Elements</span></span>

<span data-ttu-id="e1c65-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e1c65-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1c65-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e1c65-112">Parent Elements</span></span>

|<span data-ttu-id="e1c65-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1c65-113">Element</span></span>|<span data-ttu-id="e1c65-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="e1c65-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1c65-115">DefaultSettings (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="e1c65-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e1c65-116">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="e1c65-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1c65-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e1c65-117">Remarks</span></span>

<span data-ttu-id="e1c65-118">De forma predeterminada, cuando se produce un error al intentar mostrar un fragmento de datos, la ubicación de los datos se deja en blanco.</span><span class="sxs-lookup"><span data-stu-id="e1c65-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="e1c65-119">Cuando este elemento se establece en true, se mostrará la cadena de #ERR.</span><span class="sxs-lookup"><span data-stu-id="e1c65-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1c65-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="e1c65-120">See Also</span></span>

[<span data-ttu-id="e1c65-121">DefaultSettings (elemento, Format)</span><span class="sxs-lookup"><span data-stu-id="e1c65-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="e1c65-122">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1c65-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
