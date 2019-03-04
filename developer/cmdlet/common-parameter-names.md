---
title: Los nombres de parámetro comunes | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: a421d151ac3fdbb763668dd6fbf775f5b91a833f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2019
ms.locfileid: "56863651"
---
# <a name="common-parameter-names"></a>Nombres de parámetros comunes

Los parámetros descritos en este tema se conocen como *parámetros comunes de*. Que se agregan a los cmdlets, el tiempo de ejecución de Windows PowerShell y no se puede declarar mediante el cmdlet.

> [!NOTE]
> Estos parámetros se agregan también a los cmdlets de proveedor y de funciones que se decoran con el `CmdletBinding` atributo.

## <a name="general-common-parameters"></a>Parámetros comunes de general

Los parámetros siguientes se agregan a todos los cmdlets y se pueden tener acceso cada vez que se ejecuta el cmdlet. Estos parámetros se definen mediante la [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) clase.

### <a name="debug-alias-db"></a>Depurar (alias: db)

Tipo de datos: SwitchParameter

Este parámetro especifica si la depuración de nivel de programador de los mensajes que se pueden mostrar en la línea de comandos. Estos mensajes están pensados para el funcionamiento del cmdlet de solución de problemas y se generan mediante llamadas a la [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método. No es necesario localizar los mensajes de depuración.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: ea)

Tipo de datos: Enumeration

Este parámetro especifica qué acción debe tener lugar cuando se produce un error. Los valores posibles para este parámetro se definen mediante la [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeración.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: ev)

Tipo de datos: Cadena

Este parámetro especifica la variable en la que se va a colocar los objetos cuando se produce un error. Para anexar a esta variable, utilice +*varname* en lugar de borrar y establecer la variable.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Tipo de datos: Cadena

Este parámetro especifica la variable en la que se va a colocar todos los objetos generados por el cmdlet de salida. Para anexar a esta variable, utilice +*varname* en lugar de borrar y establecer la variable.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Tipo de datos: Int32

Este parámetro define el número de objetos que se almacenan en el búfer de salida antes de que todos los objetos que se pasan por la canalización. De forma predeterminada, los objetos se pasan inmediatamente por la canalización.

### <a name="verbose-alias-vb"></a>Verbose (alias: vb)

Tipo de datos: SwitchParameter

Este parámetro especifica si el cmdlet escribe mensajes explicativos que se pueden mostrar en la línea de comandos. Estos mensajes están pensados para proporcionar ayuda adicional para el usuario y se generan mediante llamadas a la [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método.

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Tipo de datos: Enumeration

Este parámetro especifica qué acción debe tener lugar cuando el cmdlet escribe un mensaje de advertencia. Los valores posibles para este parámetro se definen mediante la [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeración.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Tipo de datos: Cadena

Este parámetro especifica la variable en el que se pueden guardar los mensajes de advertencia. Para anexar a esta variable, utilice +*varname* en lugar de borrar y establecer la variable.

## <a name="risk-mitigation-parameters"></a>Parámetros de mitigación de riesgos

Los parámetros siguientes se agregan a los cmdlets que solicita confirmación antes de realizar su acción. Para obtener más información acerca de las solicitudes de confirmación, vea [solicitar confirmación](./requesting-confirmation-from-cmdlets.md). Estos parámetros se definen mediante la [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) clase.

### <a name="confirm-alias-cf"></a>Confirmar (alias: cf)

Tipo de datos: SwitchParameter

Este parámetro especifica si el cmdlet muestra un mensaje que pregunta si el usuario está seguro de que desea continuar.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Tipo de datos: SwitchParameter

Este parámetro especifica si el cmdlet escribe un mensaje que describe los efectos de ejecutar el cmdlet sin tener que realizar ninguna acción.

## <a name="transaction-parameters"></a>Parámetros de la transacción

El parámetro siguiente se agrega a los cmdlets que admiten transacciones. Estos parámetros se definen mediante la [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) clase.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Tipo de datos: SwitchParameter

Este parámetro especifica si el cmdlet usará la transacción actual para realizar su acción.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
