---
title: Errores de terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369334"
---
# <a name="terminating-errors"></a>Errores de terminación

En este tema se describe el método utilizado para notificar los errores de terminación. También se explica cómo llamar al método desde dentro del cmdlet y se describen las excepciones que puede devolver el tiempo de ejecución de Windows PowerShell cuando se llama al método.

Cuando se produce un error de terminación, el cmdlet debe notificar el error llamando al método [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Este método permite que el cmdlet envíe un registro de error que describe la condición que causó el error de terminación. Para obtener más información sobre los registros de errores, consulte [registros de errores de Windows PowerShell](./windows-powershell-error-records.md).

Cuando se llama al método [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) , el tiempo de ejecución de Windows PowerShell detiene permanentemente la ejecución de la canalización y produce una excepción [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) . Los intentos subsiguientes de llamar a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)o a otras API hacen que esas llamadas produzcan una excepción [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) .

La excepción [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) también puede producirse si otro cmdlet de la canalización informa de un error de terminación, si el usuario ha solicitado detener la canalización, o si la canalización se ha detenido antes de la finalización por cualquier motivo. No es necesario que el cmdlet detecte la excepción [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) a menos que deba limpiar los recursos abiertos o su estado interno.

Los cmdlets pueden escribir cualquier número de objetos de salida o errores de no terminación antes de notificar un error de terminación. Sin embargo, el error de terminación detiene la canalización de forma permanente y no se puede informar de los errores de salida, de terminación o de no terminación.

Los cmdlets pueden llamar a [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) solo desde el subproceso que llamó al método de procesamiento de entrada [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)o [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . No intente llamar a [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) o [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) desde otro subproceso. En su lugar, los errores se deben comunicar de vuelta al subproceso principal.

Un cmdlet puede producir una excepción en su implementación del método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)o [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Cualquier excepción que se produzca desde estos métodos (salvo algunas condiciones de error graves que detienen el host de Windows PowerShell) se interpreta como un error de terminación que detiene la canalización, pero no Windows PowerShell en su totalidad. (Esto solo se aplica al subproceso principal del cmdlet. Excepciones no detectadas en subprocesos generados por el cmdlet, en general, detenga el host de Windows PowerShell). Se recomienda usar [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) en lugar de producir una excepción, ya que el registro de errores proporciona información adicional sobre la condición de error, que es útil para el usuario final. Los cmdlets deben cumplir las instrucciones de código administrado para detectar y controlar todas las excepciones (`catch (Exception e)`). Convierta solo las excepciones de los tipos conocidos y esperados en registros de error.

## <a name="see-also"></a>Véase también

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registros de errores de Windows PowerShell](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
