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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364394"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="7d2fb-102">Parámetros de filtros de entrada</span><span class="sxs-lookup"><span data-stu-id="7d2fb-102">Input Filter Parameters</span></span>

<span data-ttu-id="7d2fb-103">Un cmdlet puede definir `Filter`, `Include`y `Exclude` parámetros que filtren el conjunto de objetos de entrada al que afecta el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="7d2fb-104">Normalmente, el conjunto de objetos de entrada se especifica mediante un parámetro `InputObject`, `Path`o `Name`.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="7d2fb-105">Por ejemplo, un cmdlet puede tener un parámetro `Path` que acepte varias rutas de acceso mediante el uso de caracteres comodín y cada ruta de acceso apunte a un objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="7d2fb-106">En conjunto, los parámetros `Filter`, `Include`y `Exclude` califican aún más las rutas de acceso en las que funciona el cmdlet cada vez que se invoca.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="7d2fb-107">Parámetros include y Exclude</span><span class="sxs-lookup"><span data-stu-id="7d2fb-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="7d2fb-108">Los parámetros `Include` y `Exclude` identifican los objetos que se incluyen o excluyen del conjunto de objetos de entrada pasados al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="7d2fb-109">Utilice estos parámetros cuando el filtro se puede expresar en el lenguaje de caracteres comodín estándar.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="7d2fb-110">(Para obtener más información sobre los caracteres comodín, vea [admitir caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)). El parámetro `Include` incluye todos los objetos cuyos nombres coinciden con el filtro de inclusión.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="7d2fb-111">El parámetro `Exclude` excluye todos los objetos cuyos nombres coinciden con el filtro.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="7d2fb-112">Parámetro de filtro</span><span class="sxs-lookup"><span data-stu-id="7d2fb-112">Filter Parameter</span></span>

<span data-ttu-id="7d2fb-113">El parámetro `Filter` especifica un filtro que no se expresa en el lenguaje de caracteres comodín estándar.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="7d2fb-114">Por ejemplo, Active Directory interfaces de servicio (ADSI) o los filtros SQL se pueden pasar al cmdlet a través de su parámetro `Filter`.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="7d2fb-115">En los cmdlets proporcionados por Windows PowerShell, estos filtros se especifican mediante los proveedores de Windows PowerShell que usan el cmdlet para tener acceso a un almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="7d2fb-116">Cada proveedor define normalmente su propio filtro.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="7d2fb-117">Filtrar si no se especifica ningún conjunto de objetos de entrada</span><span class="sxs-lookup"><span data-stu-id="7d2fb-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="7d2fb-118">Si no se especifica ningún conjunto de objetos de entrada, normalmente significa que se filtren todos los objetos.</span><span class="sxs-lookup"><span data-stu-id="7d2fb-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="7d2fb-119">Para obtener más información, vea[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="7d2fb-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d2fb-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="7d2fb-120">See Also</span></span>

[<span data-ttu-id="7d2fb-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d2fb-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)