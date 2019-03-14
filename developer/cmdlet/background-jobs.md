---
title: Trabajos en segundo plano | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794712"
---
# <a name="background-jobs"></a>Trabajos en segundo plano

Cmdlets puede llevar a cabo su acción internamente o como un en Windows PowerShell*trabajo en segundo plano*. Cuando se ejecuta un cmdlet como un trabajo en segundo plano, el trabajo se realiza de forma asincrónica en su propio subproceso independiente desde el subproceso de la canalización que usa el cmdlet. Desde la perspectiva del usuario, cuando se ejecuta un cmdlet como un trabajo en segundo plano, la línea de comandos devuelve inmediatamente incluso si el trabajo tarda un período prolongado de tiempo en completarse, y el usuario puede continuar sin interrupción mientras se ejecuta el trabajo.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Trabajos en segundo plano, los trabajos secundarios y el repositorio de trabajos

El objeto de trabajo que se devuelve mediante los cmdlets que admiten los trabajos en segundo plano define el trabajo. (El [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet también devuelve un objeto de trabajo.) El nombre del trabajo, un identificador que se usa para especificar el trabajo, la información de estado y los trabajos secundarios se incluyen en esta definición. El trabajo no realiza ninguna parte del trabajo. Cada trabajo en segundo plano tiene al menos un trabajo secundario porque el trabajo secundario realiza el trabajo real. Al ejecutar un cmdlet para que el trabajo se realiza como un trabajo en segundo plano, el cmdlet debe agregar el trabajo y los trabajos secundarios a un repositorio común, que se conoce como el *repositorio de trabajos*.

Para obtener más información acerca de cómo se controlan los trabajos en segundo plano en la línea de comandos, vea lo siguiente:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Escribir un Cmdlet que se ejecuta como un trabajo en segundo plano

Para escribir un cmdlet que se puede ejecutar como un trabajo en segundo plano, debe completar las tareas siguientes:

- Definir un `asJob` parámetro de modificador para que el usuario puede decidir si desea ejecutar el cmdlet como un trabajo en segundo plano.

- Crear un objeto que se deriva el [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) clase. Este objeto puede ser un objeto de trabajo personalizado o un objeto de trabajo proporcionados por Windows PowerShell, como un [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objeto.

- En un método de procesamiento de registro, agregue un `if` instrucción que detecta si el cmdlet debe ejecutarse como un trabajo en segundo plano.

- Para los objetos de trabajo personalizados, implemente la clase de trabajo.

- Devolver los objetos adecuados, dependiendo de si el cmdlet se ejecuta como un trabajo en segundo plano.

Para obtener un ejemplo de código, vea [compatibilidad con trabajos](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API de relacionados con los trabajos en segundo plano

Se proporcionan las siguientes API de Windows PowerShell para administrar trabajos en segundo plano.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) se deriva de los objetos de trabajo personalizado. Se trata de una clase abstracta.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) administra y proporciona información sobre los trabajos en segundo plano activo actual.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) define el estado del trabajo en segundo plano. Los Estados incluyen Started, ejecución y detenido.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) proporciona información sobre el estado de un trabajo en segundo plano y, si cambia el estado de la última fue causada por un error, el motivo por el trabajo entró en su estado actual.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) proporciona los argumentos para un evento que se provoca cuando cambia el estado de un trabajo en segundo plano.

## <a name="windows-powershell-job-cmdlets"></a>Cmdlets de trabajo de PowerShell de Windows

Se proporcionan los siguientes cmdlets de Windows PowerShell para administrar trabajos en segundo plano.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Obtiene los trabajos en segundo plano de Windows PowerShell que se están ejecutando en la sesión actual.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Obtiene los resultados de los trabajos en segundo plano de Windows PowerShell en la sesión actual.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Elimina un trabajo en segundo plano de Windows PowerShell.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Inicia un trabajo en segundo plano de Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Detiene un trabajo en segundo plano de Windows PowerShell.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Suprime el símbolo del sistema hasta que finalicen uno o todos los trabajos en segundo plano de Windows PowerShell que se ejecutan en la sesión.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
