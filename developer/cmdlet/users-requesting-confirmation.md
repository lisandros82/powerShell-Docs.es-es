---
title: Los usuarios que solicitan confirmación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856241"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="ebd05-102">Usuarios que solicitan confirmación</span><span class="sxs-lookup"><span data-stu-id="ebd05-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="ebd05-103">Cuando se especifica un valor de `true` para el `SupportsShouldProcess` parámetro de la declaración de atributo de Cmdlet, los usuarios pueden especificar el `Confirm` parámetro en el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="ebd05-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="ebd05-104">En el entorno de forma predeterminada, los usuarios pueden especificar el `Confirm` parámetro o `"-Confirm:$true` para que se solicita confirmación cuando el [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) se llama al método.</span><span class="sxs-lookup"><span data-stu-id="ebd05-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="ebd05-105">Esto omite [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) las solicitudes de confirmación, incluso para las operaciones de gran impacto.</span><span class="sxs-lookup"><span data-stu-id="ebd05-105">This bypasses [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="ebd05-106">Si `Confirm` no se especifica, el [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamada solicite confirmación si la `$ConfirmPreference` variable de preferencia es igual o mayor que el `ConfirmImpact` configuración de la cmdlet o proveedor.</span><span class="sxs-lookup"><span data-stu-id="ebd05-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="ebd05-107">El valor predeterminado de `$ConfirmPreference` es alta.</span><span class="sxs-lookup"><span data-stu-id="ebd05-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="ebd05-108">Por lo tanto, en el entorno de forma predeterminada, solo cmdlets y proveedores que especifican una acción de alto impacto solicitan confirmación.</span><span class="sxs-lookup"><span data-stu-id="ebd05-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="ebd05-109">Si `Confirm` es false o si `"-Confirm:$false` se especifica, el [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamada solicita la confirmación del usuario y el `$ConfirmPreference` se omite la variable del shell.</span><span class="sxs-lookup"><span data-stu-id="ebd05-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebd05-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ebd05-110">Remarks</span></span>

- <span data-ttu-id="ebd05-111">Para los cmdlets y proveedores que especifiquen `SupportsShouldProcess`, pero no `ConfirmImpact`, esas acciones se controlan como acciones "de impacto moderado" y no le pedirá de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ebd05-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="ebd05-112">Su nivel de impacto es menor que el valor predeterminado de la `$ConfirmPreference` variable de preferencia.</span><span class="sxs-lookup"><span data-stu-id="ebd05-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="ebd05-113">Si el usuario especifica la `Verbose` parámetro, le notificará de la operación incluso si no le pedirá confirmación.</span><span class="sxs-lookup"><span data-stu-id="ebd05-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd05-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="ebd05-114">See Also</span></span>

[<span data-ttu-id="ebd05-115">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebd05-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
