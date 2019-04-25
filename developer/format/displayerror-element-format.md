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
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066267"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="0721f-102">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="0721f-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="0721f-103">Especifica que la cadena #ERR se muestra cuando se produce un error al mostrar un elemento de datos.</span><span class="sxs-lookup"><span data-stu-id="0721f-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="0721f-104">Configuración (formato) elemento DefaultSettings (formato) DisplayError elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="0721f-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0721f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0721f-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0721f-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="0721f-106">Attributes and Elements</span></span>

<span data-ttu-id="0721f-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `DisplayError` elemento.</span><span class="sxs-lookup"><span data-stu-id="0721f-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0721f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0721f-108">Attributes</span></span>

<span data-ttu-id="0721f-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0721f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0721f-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="0721f-110">Child Elements</span></span>

<span data-ttu-id="0721f-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="0721f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0721f-112">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="0721f-112">Parent Elements</span></span>

|<span data-ttu-id="0721f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0721f-113">Element</span></span>|<span data-ttu-id="0721f-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="0721f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0721f-115">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="0721f-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="0721f-116">Define la configuración común que se aplica a todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="0721f-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0721f-117">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0721f-117">Remarks</span></span>

<span data-ttu-id="0721f-118">De forma predeterminada, cuando se produce un error al intentar mostrar un elemento de datos, la ubicación de los datos se deja en blanco.</span><span class="sxs-lookup"><span data-stu-id="0721f-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="0721f-119">Cuando este elemento se establece en true, la cadena #ERR se mostrará.</span><span class="sxs-lookup"><span data-stu-id="0721f-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0721f-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="0721f-120">See Also</span></span>

[<span data-ttu-id="0721f-121">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="0721f-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="0721f-122">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0721f-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
