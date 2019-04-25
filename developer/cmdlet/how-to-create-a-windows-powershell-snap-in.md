---
title: Cómo crear un complemento de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068001"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="82605-102">Cómo crear un complemento de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82605-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="82605-103">Un complemento de Windows PowerShell proporciona un mecanismo para registrar los conjuntos de cmdlets y el otro proveedor de Windows PowerShell con el shell, lo que permite ampliar la funcionalidad del shell.</span><span class="sxs-lookup"><span data-stu-id="82605-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="82605-104">Un complemento de Windows PowerShell puede registrar todos los cmdlets y proveedores en un único ensamblado, o puede registrar una lista específica de los cmdlets y proveedores.</span><span class="sxs-lookup"><span data-stu-id="82605-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="82605-105">Ensamblados de complementos deben instalarse en un directorio protegido, justo como se haría con otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="82605-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="82605-106">En caso contrario, los usuarios malintencionados pueden reemplazar un ensamblado con código no seguro.</span><span class="sxs-lookup"><span data-stu-id="82605-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="82605-107">Clases de complemento de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="82605-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="82605-108">Todas las clases de complemento de Windows PowerShell que se derivan de la [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) o [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) clases.</span><span class="sxs-lookup"><span data-stu-id="82605-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="82605-109">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="82605-109">Examples</span></span>

<span data-ttu-id="82605-110">[Escribir un complemento Windows PowerShell](./writing-a-windows-powershell-snap-in.md): En este ejemplo se muestra cómo crear un complemento que se usa para registrar todos los cmdlets y proveedores en un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="82605-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="82605-111">[Escribir un complemento personalizado de Windows PowerShell](./writing-a-custom-windows-powershell-snap-in.md): En este ejemplo se muestra cómo crear un complemento personalizado que se usa para registrar un conjunto específico de los cmdlets y proveedores que podrían existan o no en un único ensamblado.</span><span class="sxs-lookup"><span data-stu-id="82605-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="82605-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="82605-112">See Also</span></span>

[<span data-ttu-id="82605-113">System.Management.Automation.PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="82605-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="82605-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="82605-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="82605-115">Registrar los Cmdlets</span><span class="sxs-lookup"><span data-stu-id="82605-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="82605-116">Shell de SDK de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82605-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
