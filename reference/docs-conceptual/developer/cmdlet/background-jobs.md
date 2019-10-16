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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363564"
---
# <a name="background-jobs"></a>Trabajos en segundo plano

Los cmdlets pueden realizar su acción internamente o como un*trabajo en segundo plano*de Windows PowerShell. Cuando un cmdlet se ejecuta como un trabajo en segundo plano, el trabajo se realiza de forma asincrónica en su propio subproceso independiente del subproceso de canalización que usa el cmdlet. Desde la perspectiva del usuario, cuando un cmdlet se ejecuta como un trabajo en segundo plano, el símbolo del sistema vuelve inmediatamente, incluso si el trabajo tarda una cantidad de tiempo prolongada en completarse, y el usuario puede continuar sin interrupción mientras se ejecuta el trabajo.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Trabajos en segundo plano, trabajos secundarios y el repositorio de trabajos

El objeto de trabajo que devuelven los cmdlets que admiten trabajos en segundo plano define el trabajo. (El cmdlet [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) también devuelve un objeto de trabajo). En esta definición se incluye el nombre del trabajo, un identificador que se usa para especificar el trabajo, la información de estado y los trabajos secundarios. El trabajo no realiza ningún trabajo. Cada trabajo en segundo plano tiene al menos un trabajo secundario porque el trabajo secundario realiza el trabajo real. Al ejecutar un cmdlet para que el trabajo se realice como un trabajo en segundo plano, el cmdlet debe agregar el trabajo y los trabajos secundarios a un repositorio común, denominado repositorio de *trabajos*.

Para obtener más información sobre cómo se administran los trabajos en segundo plano en la línea de comandos, vea lo siguiente:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Escritura de un cmdlet que se ejecuta como un trabajo en segundo plano

Para escribir un cmdlet que se pueda ejecutar como un trabajo en segundo plano, debe completar las siguientes tareas:

- Defina un parámetro de modificador `asJob` para que el usuario pueda decidir si ejecutar el cmdlet como un trabajo en segundo plano.

- Cree un objeto que se derive de la clase [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) . Este objeto puede ser un objeto de trabajo personalizado o un objeto de trabajo proporcionado por Windows PowerShell, como un objeto [System. Management. Automation. Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) .

- En un método de procesamiento de registros, agregue una instrucción `if` que detecte si el cmdlet debe ejecutarse como un trabajo en segundo plano.

- En el caso de objetos de trabajo personalizados, implemente la clase Job.

- Devuelve los objetos adecuados, en función de si el cmdlet se ejecuta como un trabajo en segundo plano.

Para obtener un ejemplo de código, consulte [Cómo admitir trabajos](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API relacionadas con el trabajo en segundo plano

Windows PowerShell proporciona las siguientes API para administrar los trabajos en segundo plano.

[System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) deriva objetos de trabajo personalizados. Esta es una clase abstracta.

[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) administra y proporciona información sobre los trabajos en segundo plano activos actuales.

[System. Management. Automation. Jobstate](/dotnet/api/System.Management.Automation.JobState) define el estado del trabajo en segundo plano. Los Estados incluyen iniciado, en ejecución y detenido.

[System. Management. Automation. Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) proporciona información sobre el estado de un trabajo en segundo plano y, si el último cambio de estado fue debido a un error, la razón por la que el trabajo entró en su estado actual.

[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) proporciona los argumentos para un evento que se genera cuando un trabajo en segundo plano cambia el estado.

## <a name="windows-powershell-job-cmdlets"></a>Cmdlets de trabajo de Windows PowerShell

Windows PowerShell proporciona los siguientes cmdlets para administrar los trabajos en segundo plano.

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
