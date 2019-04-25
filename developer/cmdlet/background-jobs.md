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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068695"
---
# <a name="background-jobs"></a><span data-ttu-id="cd8d1-102">Trabajos en segundo plano</span><span class="sxs-lookup"><span data-stu-id="cd8d1-102">Background Jobs</span></span>

<span data-ttu-id="cd8d1-103">Cmdlets puede llevar a cabo su acción internamente o como un en Windows PowerShell*trabajo en segundo plano*.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="cd8d1-104">Cuando se ejecuta un cmdlet como un trabajo en segundo plano, el trabajo se realiza de forma asincrónica en su propio subproceso independiente desde el subproceso de la canalización que usa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="cd8d1-105">Desde la perspectiva del usuario, cuando se ejecuta un cmdlet como un trabajo en segundo plano, la línea de comandos devuelve inmediatamente incluso si el trabajo tarda un período prolongado de tiempo en completarse, y el usuario puede continuar sin interrupción mientras se ejecuta el trabajo.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="cd8d1-106">Trabajos en segundo plano, los trabajos secundarios y el repositorio de trabajos</span><span class="sxs-lookup"><span data-stu-id="cd8d1-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="cd8d1-107">El objeto de trabajo que se devuelve mediante los cmdlets que admiten los trabajos en segundo plano define el trabajo.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="cd8d1-108">(El [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet también devuelve un objeto de trabajo.) El nombre del trabajo, un identificador que se usa para especificar el trabajo, la información de estado y los trabajos secundarios se incluyen en esta definición.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="cd8d1-109">El trabajo no realiza ninguna parte del trabajo.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-109">The job does not perform any of the work.</span></span> <span data-ttu-id="cd8d1-110">Cada trabajo en segundo plano tiene al menos un trabajo secundario porque el trabajo secundario realiza el trabajo real.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="cd8d1-111">Al ejecutar un cmdlet para que el trabajo se realiza como un trabajo en segundo plano, el cmdlet debe agregar el trabajo y los trabajos secundarios a un repositorio común, que se conoce como el *repositorio de trabajos*.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="cd8d1-112">Para obtener más información acerca de cómo se controlan los trabajos en segundo plano en la línea de comandos, vea lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="cd8d1-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="cd8d1-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="cd8d1-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="cd8d1-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="cd8d1-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="cd8d1-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="cd8d1-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="cd8d1-116">Escribir un Cmdlet que se ejecuta como un trabajo en segundo plano</span><span class="sxs-lookup"><span data-stu-id="cd8d1-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="cd8d1-117">Para escribir un cmdlet que se puede ejecutar como un trabajo en segundo plano, debe completar las tareas siguientes:</span><span class="sxs-lookup"><span data-stu-id="cd8d1-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="cd8d1-118">Definir un `asJob` parámetro de modificador para que el usuario puede decidir si desea ejecutar el cmdlet como un trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="cd8d1-119">Crear un objeto que se deriva el [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) clase.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="cd8d1-120">Este objeto puede ser un objeto de trabajo personalizado o un objeto de trabajo proporcionados por Windows PowerShell, como un [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objeto.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="cd8d1-121">En un método de procesamiento de registro, agregue un `if` instrucción que detecta si el cmdlet debe ejecutarse como un trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="cd8d1-122">Para los objetos de trabajo personalizados, implemente la clase de trabajo.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="cd8d1-123">Devolver los objetos adecuados, dependiendo de si el cmdlet se ejecuta como un trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="cd8d1-124">Para obtener un ejemplo de código, vea [compatibilidad con trabajos](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="cd8d1-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="cd8d1-125">API de relacionados con los trabajos en segundo plano</span><span class="sxs-lookup"><span data-stu-id="cd8d1-125">Background Job-Related APIs</span></span>

<span data-ttu-id="cd8d1-126">Se proporcionan las siguientes API de Windows PowerShell para administrar trabajos en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="cd8d1-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) se deriva de los objetos de trabajo personalizado.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="cd8d1-128">Se trata de una clase abstracta.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-128">This is an abstract class.</span></span>

<span data-ttu-id="cd8d1-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) administra y proporciona información sobre los trabajos en segundo plano activo actual.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="cd8d1-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) define el estado del trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="cd8d1-131">Los Estados incluyen Started, ejecución y detenido.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="cd8d1-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) proporciona información sobre el estado de un trabajo en segundo plano y, si cambia el estado de la última fue causada por un error, el motivo por el trabajo entró en su estado actual.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="cd8d1-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) proporciona los argumentos para un evento que se provoca cuando cambia el estado de un trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="cd8d1-134">Cmdlets de trabajo de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="cd8d1-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="cd8d1-135">Se proporcionan los siguientes cmdlets de Windows PowerShell para administrar trabajos en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="cd8d1-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="cd8d1-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="cd8d1-137">Obtiene los trabajos en segundo plano de Windows PowerShell que se están ejecutando en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="cd8d1-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="cd8d1-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="cd8d1-139">Obtiene los resultados de los trabajos en segundo plano de Windows PowerShell en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="cd8d1-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="cd8d1-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="cd8d1-141">Elimina un trabajo en segundo plano de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="cd8d1-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="cd8d1-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="cd8d1-143">Inicia un trabajo en segundo plano de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="cd8d1-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="cd8d1-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="cd8d1-145">Detiene un trabajo en segundo plano de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="cd8d1-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="cd8d1-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="cd8d1-147">Suprime el símbolo del sistema hasta que finalicen uno o todos los trabajos en segundo plano de Windows PowerShell que se ejecutan en la sesión.</span><span class="sxs-lookup"><span data-stu-id="cd8d1-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd8d1-148">Véase también</span><span class="sxs-lookup"><span data-stu-id="cd8d1-148">See Also</span></span>

[<span data-ttu-id="cd8d1-149">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd8d1-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
