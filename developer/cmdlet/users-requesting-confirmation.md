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
# <a name="users-requesting-confirmation"></a>Usuarios que solicitan confirmación

Cuando se especifica un valor de `true` para el `SupportsShouldProcess` parámetro de la declaración de atributo de Cmdlet, los usuarios pueden especificar el `Confirm` parámetro en el símbolo del sistema.

En el entorno de forma predeterminada, los usuarios pueden especificar el `Confirm` parámetro o `"-Confirm:$true` para que se solicita confirmación cuando el [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) se llama al método. Esto omite [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) las solicitudes de confirmación, incluso para las operaciones de gran impacto.

Si `Confirm` no se especifica, el [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamada solicite confirmación si la `$ConfirmPreference` variable de preferencia es igual o mayor que el `ConfirmImpact` configuración de la cmdlet o proveedor. El valor predeterminado de `$ConfirmPreference` es alta. Por lo tanto, en el entorno de forma predeterminada, solo cmdlets y proveedores que especifican una acción de alto impacto solicitan confirmación.

Si `Confirm` es false o si `"-Confirm:$false` se especifica, el [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamada solicita la confirmación del usuario y el `$ConfirmPreference` se omite la variable del shell.

## <a name="remarks"></a>Observaciones

- Para los cmdlets y proveedores que especifiquen `SupportsShouldProcess`, pero no `ConfirmImpact`, esas acciones se controlan como acciones "de impacto moderado" y no le pedirá de forma predeterminada. Su nivel de impacto es menor que el valor predeterminado de la `$ConfirmPreference` variable de preferencia.

- Si el usuario especifica la `Verbose` parámetro, le notificará de la operación incluso si no le pedirá confirmación.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
