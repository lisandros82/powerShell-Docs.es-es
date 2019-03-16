---
title: La terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059242"
---
# <a name="terminating-errors"></a>Errores de terminación

Este tema describe el método utilizado para la terminación del informe. También se explica cómo llamar al método desde el cmdlet y describe las excepciones que se pueden devolver el tiempo de ejecución de Windows PowerShell cuando se llama al método.

Cuando un carácter de terminación se produce error, el cmdlet debe informar del error mediante una llamada a la [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Este método permite al cmdlet enviar un registro de error que describe la condición que provocó el error de terminación. Para obtener más información acerca de los registros de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).

Cuando el [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) se llama al método, el tiempo de ejecución de Windows PowerShell detiene la ejecución de la canalización de forma permanente y produce una [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción. Todos los intentos posteriores para llamar a [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), o varias otra API hace que las llamadas a producir un [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción.

El [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción puede producirse también si otro cmdlet en la canalización notifica un error de terminación, si el usuario solicitó detener la canalización, o si se ha detenido la canalización antes de la finalización por cualquier motivo. El cmdlet no es necesario detectar la [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción a menos que debe abrir limpiar los recursos o su estado interno.

Cmdlets puede escribir cualquier número de objetos de salida o errores de no terminación antes de informar de un error de terminación. Sin embargo, el error de terminación permanentemente detiene la canalización y ningún resultado más, la terminación, o se pueden notificar errores de no terminación.

Puede llamar los cmdlets [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) solo desde el subproceso que llama el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de procesamiento de entrada. No intente llamar a [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) desde otro subproceso. En su lugar, se deben comunicar errores hacia el subproceso principal.

Es posible que un cmdlet producir una excepción en su implementación de la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Las excepciones producidas desde estos métodos (salvo algunas condiciones de error grave que detenga el host de Windows PowerShell) se interpretan como un error de terminación que detiene la canalización, pero no de Windows PowerShell como un todo. (Esto se aplica sólo al subproceso principal del cmdlet. Las excepciones no detectadas en los subprocesos generados por el cmdlet, en general, detenga el host de Windows PowerShell.) Se recomienda que use [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) en lugar de producir una excepción porque el registro de error proporciona información adicional sobre la condición de error, lo que resulta útil para el usuario final. Los cmdlets debe respetar las directrices de código administrado frente a detectar y controlar todas las excepciones (`catch (Exception e)`). Convertir sólo las excepciones de tipos conocidos y esperados en los registros de errores.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registros de errores de PowerShell de Windows](./windows-powershell-error-records.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
