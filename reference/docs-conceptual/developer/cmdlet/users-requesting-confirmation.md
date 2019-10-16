---
title: Usuarios que solicitan confirmación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369254"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="a15f5-102">Usuarios que solicitan confirmación</span><span class="sxs-lookup"><span data-stu-id="a15f5-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="a15f5-103">Cuando se especifica un valor de `true` para el parámetro `SupportsShouldProcess` de la declaración de atributo del cmdlet, los usuarios pueden especificar el parámetro `Confirm` en el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="a15f5-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="a15f5-104">En el entorno predeterminado, los usuarios pueden especificar el parámetro `Confirm` o `"-Confirm:$true` para que se solicite la confirmación cuando se llame al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="a15f5-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="a15f5-105">Esto omite las solicitudes de confirmación de [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , incluso para las operaciones de gran impacto.</span><span class="sxs-lookup"><span data-stu-id="a15f5-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="a15f5-106">Si no se especifica `Confirm`, la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solicita confirmación si la variable de preferencia `$ConfirmPreference` es igual o mayor que la configuración de `ConfirmImpact` del cmdlet o del proveedor.</span><span class="sxs-lookup"><span data-stu-id="a15f5-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="a15f5-107">La configuración predeterminada de `$ConfirmPreference` es alta.</span><span class="sxs-lookup"><span data-stu-id="a15f5-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="a15f5-108">Por lo tanto, en el entorno predeterminado, solo los cmdlets y proveedores que especifican una confirmación de solicitud de acción de gran impacto.</span><span class="sxs-lookup"><span data-stu-id="a15f5-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="a15f5-109">Si `Confirm` es false o si se especifica `"-Confirm:$false`, la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solicita confirmación del usuario y se omite la variable de Shell `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="a15f5-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="a15f5-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a15f5-110">Remarks</span></span>

- <span data-ttu-id="a15f5-111">En el caso de los cmdlets y proveedores que especifican `SupportsShouldProcess`, pero no `ConfirmImpact`, esas acciones se administran como acciones de "impacto medio" y no se solicitarán de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a15f5-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="a15f5-112">Su nivel de impacto es menor que el valor predeterminado de la variable de preferencia `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="a15f5-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="a15f5-113">Si el usuario especifica el parámetro `Verbose`, se le notificará de la operación aunque no se le pida confirmación.</span><span class="sxs-lookup"><span data-stu-id="a15f5-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="a15f5-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="a15f5-114">See Also</span></span>

[<span data-ttu-id="a15f5-115">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a15f5-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
