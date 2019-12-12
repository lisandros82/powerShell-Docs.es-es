---
title: Creación de un cmdlet que modifica el sistema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365764"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="6d462-102">Creación de un cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="6d462-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="6d462-103">A veces, un cmdlet debe modificar el estado de ejecución del sistema, no solo el estado del tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d462-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="6d462-104">En estos casos, el cmdlet debe permitir que el usuario tenga la oportunidad de confirmar si se realiza el cambio.</span><span class="sxs-lookup"><span data-stu-id="6d462-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="6d462-105">Para admitir la confirmación, un cmdlet debe hacer dos cosas.</span><span class="sxs-lookup"><span data-stu-id="6d462-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="6d462-106">Declare que el cmdlet admita la confirmación cuando especifique el atributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) estableciendo la palabra clave SupportsShouldProcess en `true`.</span><span class="sxs-lookup"><span data-stu-id="6d462-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="6d462-107">Llame a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante la ejecución del cmdlet (como se muestra en el ejemplo siguiente).</span><span class="sxs-lookup"><span data-stu-id="6d462-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="6d462-108">Al admitir la confirmación, un cmdlet expone los parámetros `Confirm` y `WhatIf` proporcionados por Windows PowerShell y también cumple las directrices de desarrollo para los cmdlets de (para obtener más información sobre las directrices de desarrollo de cmdlets, vea [instrucciones](./cmdlet-development-guidelines.md)de desarrollo de cmdlets de).</span><span class="sxs-lookup"><span data-stu-id="6d462-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="6d462-109">Cambiar el sistema</span><span class="sxs-lookup"><span data-stu-id="6d462-109">Changing the System</span></span>

<span data-ttu-id="6d462-110">La acción de "cambiar el sistema" hace referencia a cualquier cmdlet que pueda cambiar el estado del sistema fuera de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d462-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="6d462-111">Por ejemplo, la detención de un proceso, la habilitación o deshabilitación de una cuenta de usuario o la adición de una fila a una tabla de base de datos son cambios en el sistema que deben confirmarse.</span><span class="sxs-lookup"><span data-stu-id="6d462-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="6d462-112">Por el contrario, las operaciones que leen datos o establecen conexiones transitorias no cambian el sistema y, por lo general, no requieren confirmación.</span><span class="sxs-lookup"><span data-stu-id="6d462-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="6d462-113">La confirmación tampoco es necesaria para las acciones cuyo efecto está limitado a dentro del tiempo de ejecución de Windows PowerShell, como `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="6d462-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="6d462-114">Los cmdlets que pueden o no hacer un cambio persistente deben declarar `SupportsShouldProcess` y llamar a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo si están a punto de hacer un cambio persistente.</span><span class="sxs-lookup"><span data-stu-id="6d462-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="6d462-115">La confirmación de ShouldProcess solo se aplica a los cmdlets de.</span><span class="sxs-lookup"><span data-stu-id="6d462-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="6d462-116">Si un comando o script modifica el estado de ejecución de un sistema llamando directamente a métodos o propiedades de .NET o llamando a aplicaciones fuera de Windows PowerShell, esta forma de confirmación no estará disponible.</span><span class="sxs-lookup"><span data-stu-id="6d462-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="6d462-117">El cmdlet StopProc</span><span class="sxs-lookup"><span data-stu-id="6d462-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="6d462-118">En este tema se describe un cmdlet Stop-proc que intenta detener los procesos que se recuperan con el cmdlet Get-proc (descrito en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="6d462-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="6d462-119">Definición del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d462-119">Defining the Cmdlet</span></span>

<span data-ttu-id="6d462-120">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d462-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="6d462-121">Dado que está escribiendo un cmdlet para cambiar el sistema, debe denominarse en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="6d462-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="6d462-122">Este cmdlet detiene los procesos del sistema, por lo que el nombre del verbo elegido aquí es "STOP", definido por la clase [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con el nombre "proc" para indicar que el cmdlet detiene los procesos.</span><span class="sxs-lookup"><span data-stu-id="6d462-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="6d462-123">Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="6d462-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="6d462-124">A continuación se encuentra la definición de clase para este cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="6d462-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="6d462-125">Tenga en cuenta que en la declaración de [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , la palabra clave del atributo `SupportsShouldProcess` se establece en `true` para permitir que el cmdlet realice llamadas a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="6d462-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="6d462-126">Sin esta palabra clave establecida, los parámetros `Confirm` y `WhatIf` no estarán disponibles para el usuario.</span><span class="sxs-lookup"><span data-stu-id="6d462-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="6d462-127">Acciones extremadamente destructivas</span><span class="sxs-lookup"><span data-stu-id="6d462-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="6d462-128">Algunas operaciones son extremadamente destructivas, como volver a formatear una partición del disco duro activo.</span><span class="sxs-lookup"><span data-stu-id="6d462-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="6d462-129">En estos casos, el cmdlet debe establecer `ConfirmImpact` = `ConfirmImpact.High` al declarar el atributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="6d462-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="6d462-130">Esta configuración obliga al cmdlet a solicitar la confirmación del usuario incluso cuando el usuario no ha especificado el parámetro `Confirm`.</span><span class="sxs-lookup"><span data-stu-id="6d462-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="6d462-131">Sin embargo, los desarrolladores de cmdlets deben evitar sobreutilizar `ConfirmImpact` para las operaciones que son potencialmente destructivas, como eliminar una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="6d462-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="6d462-132">Recuerde que si `ConfirmImpact` está establecido en [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span><span class="sxs-lookup"><span data-stu-id="6d462-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="6d462-133">De forma similar, es poco probable que algunas operaciones sean destructivas, aunque en teoría modifican el estado de ejecución de un sistema fuera de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d462-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="6d462-134">Estos cmdlets pueden establecer `ConfirmImpact` en [System. Management. Automation. Confirmimpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="6d462-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="6d462-135">Esto omitirá las solicitudes de confirmación en las que el usuario ha solicitado confirmar solo las operaciones de impacto medio y alto impacto.</span><span class="sxs-lookup"><span data-stu-id="6d462-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="6d462-136">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="6d462-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="6d462-137">En esta sección se describe cómo definir los parámetros del cmdlet, incluidos los que son necesarios para admitir la modificación del sistema.</span><span class="sxs-lookup"><span data-stu-id="6d462-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="6d462-138">Consulte [agregar parámetros que procesan la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md) si necesita información general sobre la definición de parámetros.</span><span class="sxs-lookup"><span data-stu-id="6d462-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="6d462-139">El cmdlet Stop-proc define tres parámetros: `Name`, `Force`y `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="6d462-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="6d462-140">El parámetro `Name` corresponde a la propiedad `Name` del objeto de entrada del proceso.</span><span class="sxs-lookup"><span data-stu-id="6d462-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="6d462-141">Tenga en cuenta que el parámetro `Name` de este ejemplo es obligatorio, ya que se producirá un error en el cmdlet si no tiene un proceso con nombre para detenerse.</span><span class="sxs-lookup"><span data-stu-id="6d462-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="6d462-142">El parámetro `Force` permite al usuario invalidar las llamadas a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="6d462-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="6d462-143">De hecho, cualquier cmdlet que llama a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) debe tener un parámetro `Force` de modo que, cuando se especifica `Force`, el cmdlet omite la llamada a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) y continúa con la operación.</span><span class="sxs-lookup"><span data-stu-id="6d462-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="6d462-144">Tenga en cuenta que esto no afecta a las llamadas a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="6d462-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="6d462-145">El parámetro `PassThru` permite al usuario indicar si el cmdlet pasa un objeto de salida a través de la canalización, en este caso, después de que se detenga un proceso.</span><span class="sxs-lookup"><span data-stu-id="6d462-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="6d462-146">Tenga en cuenta que este parámetro está asociado al propio cmdlet en lugar de a una propiedad del objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="6d462-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="6d462-147">Esta es la declaración de parámetro para el cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="6d462-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="6d462-148">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="6d462-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="6d462-149">El cmdlet debe invalidar un método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="6d462-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="6d462-150">En el código siguiente se muestra la invalidación [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) usada en el cmdlet Stop-proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6d462-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="6d462-151">Para cada nombre de proceso solicitado, este método garantiza que el proceso no es un proceso especial, intenta detener el proceso y, a continuación, envía un objeto de salida si se especifica el parámetro `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="6d462-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="6d462-152">Llamar al método ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="6d462-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="6d462-153">El método de procesamiento de entrada del cmdlet debe llamar al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para confirmar la ejecución de una operación antes de que se realice un cambio (por ejemplo, la eliminación de archivos) en el estado de ejecución del sistema.</span><span class="sxs-lookup"><span data-stu-id="6d462-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="6d462-154">Esto permite que el tiempo de ejecución de Windows PowerShell proporcione el comportamiento correcto de "WhatIf" y "CONFIRM" dentro del shell.</span><span class="sxs-lookup"><span data-stu-id="6d462-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="6d462-155">Si un cmdlet indica que admite debe procesar y no puede realizar la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , el usuario podría modificar el sistema de forma inesperada.</span><span class="sxs-lookup"><span data-stu-id="6d462-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="6d462-156">La llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia para determinar lo que se debe mostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="6d462-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="6d462-157">En el ejemplo siguiente se muestra la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en el cmdlet Stop-proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6d462-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="6d462-158">Llamar al método ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="6d462-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="6d462-159">La llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) envía un mensaje secundario al usuario.</span><span class="sxs-lookup"><span data-stu-id="6d462-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="6d462-160">Esta llamada se realiza después de que la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devuelva `true` y si el parámetro `Force` no se estableció en `true`.</span><span class="sxs-lookup"><span data-stu-id="6d462-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="6d462-161">A continuación, el usuario puede proporcionar comentarios para indicar si la operación debe continuar.</span><span class="sxs-lookup"><span data-stu-id="6d462-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="6d462-162">El cmdlet llama a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como una comprobación adicional para las modificaciones potencialmente peligrosas del sistema o cuando desea proporcionar al usuario opciones de sí a todo y de no a todos.</span><span class="sxs-lookup"><span data-stu-id="6d462-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="6d462-163">En el ejemplo siguiente se muestra la llamada a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en el cmdlet Stop-proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6d462-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="6d462-164">Detener el procesamiento de la entrada</span><span class="sxs-lookup"><span data-stu-id="6d462-164">Stopping Input Processing</span></span>

<span data-ttu-id="6d462-165">El método de procesamiento de entrada de un cmdlet que realiza modificaciones en el sistema debe proporcionar una manera de detener el procesamiento de la entrada.</span><span class="sxs-lookup"><span data-stu-id="6d462-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="6d462-166">En el caso de este cmdlet Stop-proc, se realiza una llamada desde el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) al método [System. Diagnostics. Process. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="6d462-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="6d462-167">Dado que el parámetro `PassThru` está establecido en `true`, [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) también llama a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar el objeto de proceso a la canalización.</span><span class="sxs-lookup"><span data-stu-id="6d462-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6d462-168">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="6d462-168">Code Sample</span></span>

<span data-ttu-id="6d462-169">Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6d462-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="6d462-170">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="6d462-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="6d462-171">Windows PowerShell pasa información entre cmdlets mediante objetos .net.</span><span class="sxs-lookup"><span data-stu-id="6d462-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="6d462-172">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d462-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="6d462-173">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="6d462-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="6d462-174">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d462-174">Building the Cmdlet</span></span>

<span data-ttu-id="6d462-175">Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d462-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="6d462-176">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="6d462-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="6d462-177">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d462-177">Testing the Cmdlet</span></span>

<span data-ttu-id="6d462-178">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="6d462-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="6d462-179">A continuación se muestran varias pruebas que prueban el cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="6d462-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="6d462-180">Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="6d462-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="6d462-181">Inicie Windows PowerShell y use el cmdlet Stop-proc para detener el procesamiento, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="6d462-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="6d462-182">Dado que el cmdlet especifica el parámetro `Name` como obligatorio, el cmdlet consulta el parámetro.</span><span class="sxs-lookup"><span data-stu-id="6d462-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="6d462-183">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="6d462-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="6d462-184">Ahora vamos a usar el cmdlet para detener el proceso denominado "NOTEPAD".</span><span class="sxs-lookup"><span data-stu-id="6d462-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="6d462-185">El cmdlet le pide que confirme la acción.</span><span class="sxs-lookup"><span data-stu-id="6d462-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="6d462-186">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="6d462-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="6d462-187">Use STOP-proc como se muestra para detener el proceso crítico denominado "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="6d462-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="6d462-188">Se le pedirá que le avise sobre cómo realizar esta acción porque hará que el sistema operativo se reinicie.</span><span class="sxs-lookup"><span data-stu-id="6d462-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="6d462-189">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="6d462-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="6d462-190">Ahora vamos a intentar detener el proceso WINLOGON sin recibir una advertencia.</span><span class="sxs-lookup"><span data-stu-id="6d462-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="6d462-191">Tenga en cuenta que esta entrada de comando usa el parámetro `Force` para invalidar la advertencia.</span><span class="sxs-lookup"><span data-stu-id="6d462-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="6d462-192">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="6d462-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="6d462-193">Véase también</span><span class="sxs-lookup"><span data-stu-id="6d462-193">See Also</span></span>

[<span data-ttu-id="6d462-194">Agregar parámetros que procesan la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="6d462-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="6d462-195">[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6d462-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="6d462-196">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6d462-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="6d462-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6d462-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6d462-198">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d462-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)