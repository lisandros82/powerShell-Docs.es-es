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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054364"
---
# <a name="non-terminating-errors"></a>Errores de no terminación

En este tema se describe el método utilizado para notificar errores de no terminación. También se explica cómo llamar al método desde el cmdlet.

Cuando se produce un error de no terminación, el cmdlet debe informar de este error mediante una llamada a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método. Cuando el cmdlet notifica un error de no terminación, el cmdlet puede seguir funcionando en este objeto de entrada y en la entrada más objetos de canalización. Si el cmdlet llama a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, el cmdlet puede escribir un registro de error que describe la condición que provocó el error de no terminación. Para obtener más información acerca de los registros de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).

Puede llamar los cmdlets [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) según sea necesario desde dentro de su métodos de procesamiento de entrada. Sin embargo, puede llamar los cmdlets [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo desde el subproceso que llama el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de procesamiento de entrada. No llame a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) desde otro subproceso. En su lugar, comunicar errores hacia el subproceso principal.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Registros de errores de PowerShell de Windows](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
