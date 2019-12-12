---
title: Nombres de parámetros comunes | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365744"
---
# <a name="common-parameter-names"></a>Nombres de parámetros comunes

Los parámetros que se describen en este tema se conocen como *parámetros comunes*. Se agregan a los cmdlets mediante el tiempo de ejecución de Windows PowerShell y no se pueden declarar mediante el cmdlet.

> [!NOTE]
> Estos parámetros también se agregan a los cmdlets de proveedor y a las funciones que se decoran con el atributo `CmdletBinding`.

## <a name="general-common-parameters"></a>Parámetros comunes generales

Los parámetros siguientes se agregan a todos los cmdlets y se puede tener acceso a ellos cada vez que se ejecuta el cmdlet. Estos parámetros se definen mediante la clase [System. Management. Automation. Internal. Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) .

### <a name="debug-alias-db"></a>Debug (alias: DB)

Tipo de datos: Parámetrodemodificador

Este parámetro especifica si los mensajes de depuración de nivel de programador se pueden mostrar en la línea de comandos. Estos mensajes están diseñados para solucionar problemas del funcionamiento del cmdlet y se generan mediante llamadas al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . No es necesario localizar los mensajes de depuración.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: EA)

Tipo de datos: enumeración

Este parámetro especifica qué acción se debe realizar cuando se produce un error. Los valores posibles para este parámetro se definen mediante la enumeración [System. Management. Automation. Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: EV)

Tipo de datos: cadena

Este parámetro especifica la variable en la que se colocan los objetos cuando se produce un error. Para anexar a esta variable, use +*varname* en lugar de borrar y establecer la variable.

### <a name="outvariable-alias-ov"></a>Outvariable (alias: OT)

Tipo de datos: cadena

Este parámetro especifica la variable en la que se colocan todos los objetos de salida generados por el cmdlet. Para anexar a esta variable, use +*varname* en lugar de borrar y establecer la variable.

### <a name="outbuffer-alias-ob"></a>Outbuffer (alias: OB)

Tipo de datos: Int32

Este parámetro define el número de objetos que se almacenan en el búfer de salida antes de que los objetos se pasen por la canalización. De forma predeterminada, los objetos se pasan inmediatamente hacia abajo en la canalización.

### <a name="verbose-alias-vb"></a>Verbose (alias: VB)

Tipo de datos: Parámetrodemodificador

Este parámetro especifica si el cmdlet escribe mensajes explicativos que se pueden mostrar en la línea de comandos. Estos mensajes están diseñados para proporcionar ayuda adicional al usuario y se generan mediante llamadas al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

### <a name="warningaction-alias-wa"></a>WarningAction (alias: WA)

Tipo de datos: enumeración

Este parámetro especifica la acción que debe llevarse a cabo cuando el cmdlet escribe un mensaje de advertencia. Los valores posibles para este parámetro se definen mediante la enumeración [System. Management. Automation. Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: WV)

Tipo de datos: cadena

Este parámetro especifica la variable en la que se pueden guardar los mensajes de advertencia. Para anexar a esta variable, use +*varname* en lugar de borrar y establecer la variable.

## <a name="risk-mitigation-parameters"></a>Parámetros de mitigación de riesgos

Los parámetros siguientes se agregan a los cmdlets que solicitan confirmación antes de realizar su acción. Para obtener más información acerca de las solicitudes de confirmación, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md). Estos parámetros se definen mediante la clase [System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) .

### <a name="confirm-alias-cf"></a>Confirmar (alias: CF)

Tipo de datos: Parámetrodemodificador

Este parámetro especifica si el cmdlet muestra un mensaje que pregunta si el usuario está seguro de que desea continuar.

### <a name="whatif-alias-wi"></a>WhatIf (alias: Wi)

Tipo de datos: Parámetrodemodificador

Este parámetro especifica si el cmdlet escribe un mensaje que describe los efectos de ejecutar el cmdlet sin realizar ninguna acción.

## <a name="transaction-parameters"></a>Parámetros de transacción

El parámetro siguiente se agrega a los cmdlets que admiten transacciones. Estos parámetros se definen mediante la clase [System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) .

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Tipo de datos: Parámetrodemodificador

Este parámetro especifica si el cmdlet usará la transacción actual para realizar su acción.

## <a name="see-also"></a>Véase también

[System. Management. Automation. Internal. Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
