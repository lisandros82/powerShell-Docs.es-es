---
title: Conceptos de los informes de errores | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054414"
---
# <a name="error-reporting-concepts"></a>Conceptos de los informes de errores

Windows PowerShell proporciona dos mecanismos para notificar errores: un mecanismo para *la terminación* y otro mecanismo para *errores de no terminación*. Es importante para el cmdlet para notificar los errores correctamente para que la aplicación host que se está ejecutando los cmdlets puede reaccionar de manera adecuada.

El cmdlet debe llamar a la [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método cuando produce un error que no tiene o no debe permitir que el cmdlet para continuar procesando sus objetos de entrada. El cmdlet debe llamar a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para informar de errores de no terminación cuando el cmdlet puede continuar procesando los objetos de entrada. Ambos métodos proporcionan un registro de errores que la aplicación host puede utilizar para investigar la causa del error.

Utilice las siguientes directrices para determinar si un error es un carácter de terminación o error de no terminación.

- Un error es un error de terminación si impide que el cmdlet dejar de procesar el objeto actual o procesar correctamente los objetos de entrada aún más, independientemente de su contenido.

- Un error es un error de terminación si no desea que el cmdlet para continuar procesando el objeto actual o cualquier objeto de entrada adicional, independientemente de su contenido.

- Un error es un error de terminación si se produce en un cmdlet que no se aceptan o devuelven un objeto o si se produce en un cmdlet que acepte o devuelve un único objeto.

- Un error es un error de no terminación si desea que el cmdlet para continuar procesando el objeto actual y los objetos aún más la entrada.

- Un error es un error de no terminación si está relacionado con un objeto de entrada específico o un subconjunto de objetos de entrada.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registros de errores de PowerShell de Windows](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
