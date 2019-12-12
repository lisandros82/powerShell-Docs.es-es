---
title: Conceptos de informes de errores | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364624"
---
# <a name="error-reporting-concepts"></a>Conceptos de los informes de errores

Windows PowerShell proporciona dos mecanismos para notificar errores: un mecanismo para *Finalizar errores* y otro mecanismo para *errores de no terminación*. Es importante que el cmdlet informe de los errores correctamente para que la aplicación host que ejecuta los cmdlets pueda reaccionar de manera adecuada.

El cmdlet debe llamar al método [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) cuando se produce un error que no permite que el cmdlet continúe procesando sus objetos de entrada. El cmdlet debe llamar al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación cuando el cmdlet puede seguir procesando los objetos de entrada. Ambos métodos proporcionan un registro de errores que la aplicación host puede usar para investigar la causa del error.

Utilice las siguientes directrices para determinar si un error es un error de terminación o de no terminación.

- Un error es un error de terminación si impide que el cmdlet continúe procesando el objeto actual o procesa correctamente cualquier otro objeto de entrada, independientemente de su contenido.

- Un error es un error de terminación si no desea que el cmdlet continúe procesando el objeto actual o cualquier otro objeto de entrada, independientemente de su contenido.

- Un error es un error de terminación en caso de que se produzca en un cmdlet que no acepte o devuelva un objeto o que se produzca en un cmdlet que acepte o devuelva un solo objeto.

- Un error es un error de no terminación si desea que el cmdlet siga procesando el objeto actual y los objetos de entrada adicionales.

- Un error es un error de no terminación si está relacionado con un objeto de entrada o un subconjunto de objetos de entrada específicos.

## <a name="see-also"></a>Véase también

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registros de errores de Windows PowerShell](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
