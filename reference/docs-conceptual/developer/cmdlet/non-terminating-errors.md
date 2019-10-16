---
title: Errores de no terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369604"
---
# <a name="non-terminating-errors"></a>Errores de no terminación

En este tema se describe el método utilizado para notificar los errores de no terminación. También se explica cómo llamar al método desde dentro del cmdlet.

Cuando se produce un error de no terminación, el cmdlet debe notificar este error llamando al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) . Cuando el cmdlet informa de un error de no terminación, el cmdlet puede seguir operando en este objeto de entrada y en objetos de canalización de entrada adicionales. Si el cmdlet llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , el cmdlet puede escribir un registro de error que describa la condición que provocó el error de no terminación. Para obtener más información sobre los registros de errores, consulte [registros de errores de Windows PowerShell](./windows-powershell-error-records.md).

Los cmdlets pueden llamar a [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) según sea necesario desde los métodos de procesamiento de entrada. Sin embargo, los cmdlets pueden llamar a [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo desde el subproceso que llamó a [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o método de procesamiento de entrada [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . No llame a [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) desde otro subproceso. En su lugar, comunique los errores de vuelta al subproceso principal.

## <a name="see-also"></a>Véase también

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Registros de errores de Windows PowerShell](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
