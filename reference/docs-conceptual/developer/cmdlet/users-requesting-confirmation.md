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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369254"
---
# <a name="users-requesting-confirmation"></a>Usuarios que solicitan confirmación

Cuando se especifica un valor de `true` para el parámetro `SupportsShouldProcess` de la declaración de atributo del cmdlet, los usuarios pueden especificar el parámetro `Confirm` en el símbolo del sistema.

En el entorno predeterminado, los usuarios pueden especificar el `Confirm` parámetro o `"-Confirm:$true` para que se solicite la confirmación cuando se llame al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Esto omite las solicitudes de confirmación de [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , incluso para las operaciones de gran impacto.

Si no se especifica `Confirm`, la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solicita confirmación si la variable de preferencia de `$ConfirmPreference` es igual o mayor que la configuración de `ConfirmImpact` del cmdlet o del proveedor. La configuración predeterminada de `$ConfirmPreference` es alta. Por lo tanto, en el entorno predeterminado, solo los cmdlets y proveedores que especifican una confirmación de solicitud de acción de gran impacto.

Si `Confirm` es false o si se especifica `"-Confirm:$false`, la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solicita confirmación del usuario y se omite la variable de Shell `$ConfirmPreference`.

## <a name="remarks"></a>Observaciones

- En el caso de los cmdlets y proveedores que especifican `SupportsShouldProcess`, pero no `ConfirmImpact`, esas acciones se controlan como acciones de "impacto medio", y no se solicitarán de forma predeterminada. Su nivel de impacto es menor que el valor predeterminado de la variable de preferencia `$ConfirmPreference`.

- Si el usuario especifica el parámetro `Verbose`, se le notificará de la operación aunque no se le pida confirmación.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
