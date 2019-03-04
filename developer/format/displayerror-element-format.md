---
title: Elemento DisplayError (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854921"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="4d111-102">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="4d111-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="4d111-103">Especifica que la cadena #ERR se muestra cuando se produce un error al mostrar un elemento de datos.</span><span class="sxs-lookup"><span data-stu-id="4d111-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="4d111-104">Configuración (formato) elemento DefaultSettings (formato) DisplayError elemento (Frmat)</span><span class="sxs-lookup"><span data-stu-id="4d111-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d111-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4d111-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d111-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="4d111-106">Attributes and Elements</span></span>

<span data-ttu-id="4d111-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `DisplayError` elemento.</span><span class="sxs-lookup"><span data-stu-id="4d111-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d111-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="4d111-108">Attributes</span></span>

<span data-ttu-id="4d111-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4d111-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d111-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="4d111-110">Child Elements</span></span>

<span data-ttu-id="4d111-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="4d111-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4d111-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="4d111-112">Parent Elements</span></span>

|<span data-ttu-id="4d111-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4d111-113">Element</span></span>|<span data-ttu-id="4d111-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d111-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d111-115">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="4d111-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="4d111-116">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="4d111-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4d111-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4d111-117">Remarks</span></span>

<span data-ttu-id="4d111-118">De forma predeterminada, cuando se produce un error al intentar mostrar un elemento de datos, la ubicación de los datos se deja en blanco.</span><span class="sxs-lookup"><span data-stu-id="4d111-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="4d111-119">Cuando este elemento se establece en true, la cadena #ERR se mostrará.</span><span class="sxs-lookup"><span data-stu-id="4d111-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d111-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="4d111-120">See Also</span></span>

[<span data-ttu-id="4d111-121">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="4d111-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="4d111-122">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d111-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
