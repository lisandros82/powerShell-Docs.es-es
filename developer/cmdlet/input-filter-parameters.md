---
title: Parámetros de filtro de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854471"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="8a1d4-102">Parámetros de filtros de entrada</span><span class="sxs-lookup"><span data-stu-id="8a1d4-102">Input Filter Parameters</span></span>

<span data-ttu-id="8a1d4-103">Puede definir un cmdlet `Filter`, `Include`, y `Exclude` los parámetros que filtran el conjunto de objetos de entrada que afecta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="8a1d4-104">Normalmente, el conjunto de objetos de entrada especificado por un `InputObject`, `Path`, o `Name` parámetro.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="8a1d4-105">Por ejemplo, un cmdlet puede tener un `Path` parámetro que acepta varias rutas de acceso mediante el uso de caracteres comodín y los puntos de cada ruta de acceso a un objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="8a1d4-106">Utilizar juntos, el `Filter`, `Include`, y `Exclude` más parámetros calificar las rutas de acceso que el cmdlet funciona en cada vez que se invoca.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="8a1d4-107">Incluir y excluir los parámetros</span><span class="sxs-lookup"><span data-stu-id="8a1d4-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="8a1d4-108">El `Include` y `Exclude` parámetros identifican los objetos que se incluyen o excluyen del conjunto de objetos de entrada pasado al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="8a1d4-109">Use estos parámetros cuando el filtro se puede expresar en el lenguaje de comodín estándar.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="8a1d4-110">(Para obtener más información sobre los caracteres comodín, consulte [que admiten caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) El `Include` parámetro incluye todos los objetos cuyos nombres coincidan con el filtro de inclusión.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="8a1d4-111">El `Exclude` parámetro excluye todos los objetos cuyos nombres coincidan con el filtro.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="8a1d4-112">Parámetro de filtro</span><span class="sxs-lookup"><span data-stu-id="8a1d4-112">Filter Parameter</span></span>

<span data-ttu-id="8a1d4-113">El `Filter` parámetro especifica un filtro que no se expresa en el lenguaje de comodín estándar.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="8a1d4-114">Por ejemplo, los filtros de las Interfaces de servicio de Active Directory (ADSI) o SQL podrían pasarse al cmdlet a través de su `Filter` parámetro.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="8a1d4-115">En los cmdlets proporcionados por Windows PowerShell, estos filtros se especifican mediante los proveedores de Windows PowerShell que use el cmdlet para obtener acceso a un almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="8a1d4-116">Cada proveedor normalmente define su propio filtro.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="8a1d4-117">Si no se especifica ningún conjunto de objetos de entrada de filtrado</span><span class="sxs-lookup"><span data-stu-id="8a1d4-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="8a1d4-118">Si no se especifica ningún conjunto de objetos de entrada, normalmente esto significa que se filtrará todos los objetos.</span><span class="sxs-lookup"><span data-stu-id="8a1d4-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="8a1d4-119">Para obtener más información, consulte[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="8a1d4-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a1d4-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="8a1d4-120">See Also</span></span>

[<span data-ttu-id="8a1d4-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a1d4-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)