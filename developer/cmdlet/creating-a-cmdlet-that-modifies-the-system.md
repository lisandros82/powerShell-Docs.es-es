---
title: Creación de un Cmdlet que modifica el sistema | Microsoft Docs
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
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055145"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="3e388-102">Creación de un cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="3e388-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="3e388-103">A veces, un cmdlet debe modificar el estado de ejecución del sistema, no solo el estado del tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e388-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="3e388-104">En estos casos, el cmdlet debe permitir al usuario una oportunidad de confirmar si desea realizar el cambio o no.</span><span class="sxs-lookup"><span data-stu-id="3e388-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="3e388-105">Para admitir la confirmación de un cmdlet debe hacer dos cosas.</span><span class="sxs-lookup"><span data-stu-id="3e388-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="3e388-106">Declarar que el cmdlet admite confirmación cuando se especifica la [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo estableciendo la palabra clave SupportsShouldProcess en `true`.</span><span class="sxs-lookup"><span data-stu-id="3e388-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="3e388-107">Llame a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante la ejecución del cmdlet (como se muestra en el ejemplo siguiente).</span><span class="sxs-lookup"><span data-stu-id="3e388-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="3e388-108">Admitiendo la confirmación, se expone un cmdlet el `Confirm` y `WhatIf` parámetros que se proporcionan mediante Windows PowerShell y también con las directrices de desarrollo de cmdlets (para obtener más información acerca de las instrucciones de desarrollo de cmdlet, consulte [ Las instrucciones de desarrollo de cmdlet](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="3e388-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="3e388-109">Cambio del sistema</span><span class="sxs-lookup"><span data-stu-id="3e388-109">Changing the System</span></span>

<span data-ttu-id="3e388-110">El acto de "cambiar el sistema" hace referencia a cualquier cmdlet que potencialmente se cambia el estado del sistema fuera de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e388-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="3e388-111">Por ejemplo, detener un proceso, habilitar o deshabilitar una cuenta de usuario o agregar una fila a una tabla de base de datos son todos los cambios en el sistema que se debe confirmar.</span><span class="sxs-lookup"><span data-stu-id="3e388-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="3e388-112">En cambio, las operaciones que leerán los datos o establecer las conexiones transitorias no cambian el sistema y generalmente no requieren confirmación.</span><span class="sxs-lookup"><span data-stu-id="3e388-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="3e388-113">Confirmación también no es necesaria para las acciones cuyo efecto se limita a dentro del tiempo de ejecución de Windows PowerShell, como `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="3e388-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="3e388-114">Debe declarar los cmdlets que puede o no se puede hacer un cambio definitivo `SupportsShouldProcess` y llamar a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo si va a realizar un cambio definitivo.</span><span class="sxs-lookup"><span data-stu-id="3e388-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="3e388-115">Confirmación de ShouldProcess se aplica únicamente a los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3e388-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="3e388-116">Si un comando o script modifica el estado de ejecución de un sistema llamando directamente a propiedades o métodos. NET, o por aplicaciones que realizan llamadas fuera de Windows PowerShell, esta forma de confirmación no estará disponible.</span><span class="sxs-lookup"><span data-stu-id="3e388-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="3e388-117">El StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="3e388-118">Este tema describe un cmdlet Stop-Proc que intenta detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="3e388-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="3e388-119">Temas de esta sección incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3e388-119">Topics in this section include the following:</span></span>

- [<span data-ttu-id="3e388-120">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-120">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="3e388-121">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="3e388-121">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="3e388-122">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3e388-122">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="3e388-123">Una llamada al método ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="3e388-123">Calling the ShouldProcess Method</span></span>](#Calling-the-ShouldProcess-Method)

- [<span data-ttu-id="3e388-124">Una llamada al método ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="3e388-124">Calling the ShouldContinue Method</span></span>](#Calling-the-ShouldContinue-Method)

- [<span data-ttu-id="3e388-125">Detener procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3e388-125">Stopping Input Processing</span></span>](#Stopping-Input-Processing)

- [<span data-ttu-id="3e388-126">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="3e388-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="3e388-127">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="3e388-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="3e388-128">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-128">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="3e388-129">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-129">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="3e388-130">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-130">Defining the Cmdlet</span></span>

<span data-ttu-id="3e388-131">El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e388-131">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="3e388-132">Dado que está escribiendo un cmdlet para cambiar el sistema, debe llamarse en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="3e388-132">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="3e388-133">Este procesos del sistema se detiene de cmdlet, por lo que el nombre del verbo seleccionado aquí es "Stop" definen por el [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (clase), con el sustantivo "Proc" para indicar que el cmdlet detiene los procesos.</span><span class="sxs-lookup"><span data-stu-id="3e388-133">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="3e388-134">Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3e388-134">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3e388-135">La siguiente es la definición de clase para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3e388-135">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="3e388-136">Tenga en cuenta que, en el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaración, el `SupportsShouldProcess` palabra clave de atributo está establecido en `true` para habilitar el cmdlet realizar llamadas a [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="3e388-136">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="3e388-137">Sin este conjunto de palabra clave, el `Confirm` y `WhatIf` parámetros no estarán disponibles para el usuario.</span><span class="sxs-lookup"><span data-stu-id="3e388-137">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="3e388-138">Acciones destructivas extremadamente</span><span class="sxs-lookup"><span data-stu-id="3e388-138">Extremely Destructive Actions</span></span>

<span data-ttu-id="3e388-139">Algunas operaciones son extremadamente destructivas, como volver a formatear una partición de disco duro activo.</span><span class="sxs-lookup"><span data-stu-id="3e388-139">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="3e388-140">En estos casos, debe establecer el cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` al declarar el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo.</span><span class="sxs-lookup"><span data-stu-id="3e388-140">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="3e388-141">Esta opción fuerza el cmdlet para solicitar la confirmación de usuario incluso cuando el usuario no ha especificado el `Confirm` parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e388-141">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="3e388-142">Sin embargo, los desarrolladores de cmdlets deben evitar el uso excesivo `ConfirmImpact` para las operaciones que son simplemente potencialmente destructivas, como la eliminación de una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="3e388-142">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="3e388-143">Recuerde que si `ConfirmImpact` está establecido en [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="3e388-143">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="3e388-144">De forma similar, algunas operaciones suelen ser destructivo, aunque en teoría modifican el estado de ejecución de un sistema fuera de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e388-144">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="3e388-145">Puede establecer estos cmdlets `ConfirmImpact` a [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="3e388-145">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="3e388-146">Esto pasará por alto las solicitudes de confirmación que ha solicitado el usuario para confirmar las operaciones solo impacto medio y alto impacto.</span><span class="sxs-lookup"><span data-stu-id="3e388-146">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="3e388-147">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="3e388-147">Defining Parameters for System Modification</span></span>

<span data-ttu-id="3e388-148">En esta sección se describe cómo definir los parámetros del cmdlet, las que son necesarios para la modificación del sistema de soporte técnico incluidas.</span><span class="sxs-lookup"><span data-stu-id="3e388-148">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="3e388-149">Consulte [agregar parámetros esa entrada de línea de comandos de proceso](./adding-parameters-that-process-command-line-input.md) si necesita obtener información general acerca de cómo definir parámetros.</span><span class="sxs-lookup"><span data-stu-id="3e388-149">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="3e388-150">El cmdlet Stop-Proc define tres parámetros: `Name`, `Force`, y `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="3e388-150">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="3e388-151">El `Name` parámetro corresponde a la `Name` propiedad del objeto de entrada de proceso.</span><span class="sxs-lookup"><span data-stu-id="3e388-151">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="3e388-152">Tenga en cuenta que el `Name` parámetro en este ejemplo es obligatorio, como el cmdlet se producirá un error si no tiene un proceso con nombre a detener.</span><span class="sxs-lookup"><span data-stu-id="3e388-152">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="3e388-153">El `Force` parámetro permite al usuario reemplazar las llamadas a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="3e388-153">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="3e388-154">De hecho, cualquier cmdlet que llama [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) debe tener un `Force` parámetro para que cuando `Force` se especifica, el cmdlet omite la llamada a [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) y continúa con la operación.</span><span class="sxs-lookup"><span data-stu-id="3e388-154">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="3e388-155">Tenga en cuenta que esto no afecta a las llamadas a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="3e388-155">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="3e388-156">El `PassThru` parámetro permite al usuario indicar si el cmdlet pasa un objeto de salida a través de la canalización, en este caso, cuando se haya detenido un proceso.</span><span class="sxs-lookup"><span data-stu-id="3e388-156">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="3e388-157">Tenga en cuenta que este parámetro está relacionado con el cmdlet propia en lugar de a una propiedad del objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e388-157">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="3e388-158">Aquí es la declaración de parámetro para el cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3e388-158">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3e388-159">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3e388-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3e388-160">El cmdlet debe invalidar una método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e388-160">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="3e388-161">El código siguiente ilustra la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) invalidación que se usa en el cmdlet Stop-Proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="3e388-161">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="3e388-162">Para cada uno solicita el nombre del proceso, este método garantiza que el proceso no es un proceso especial, intenta detener el proceso y, a continuación, envía un objeto de salida si el `PassThru` se especifica el parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e388-162">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="3e388-163">Una llamada al método ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="3e388-163">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="3e388-164">El método de su cmdlet de procesamiento de entrada debe llamar a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para confirmar la ejecución de una operación antes de que se realiza un cambio (por ejemplo, la eliminación de archivos) en el estado de ejecución del sistema.</span><span class="sxs-lookup"><span data-stu-id="3e388-164">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="3e388-165">Esto permite que el tiempo de ejecución de Windows PowerShell proporcionar el comportamiento correcto de "WhatIf" y "Confirmar" en el shell.</span><span class="sxs-lookup"><span data-stu-id="3e388-165">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="3e388-166">Si un cmdlet indica que es compatible con debe procesar y se produce un error al realizar la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamar a, el usuario podría modificar el sistema de forma inesperada.</span><span class="sxs-lookup"><span data-stu-id="3e388-166">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="3e388-167">La llamada a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia determinar lo que debe mostrarse al usuario.</span><span class="sxs-lookup"><span data-stu-id="3e388-167">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="3e388-168">El ejemplo siguiente muestra la llamada a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de reemplazar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método en el ejemplo Cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3e388-168">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="3e388-169">Una llamada al método ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="3e388-169">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="3e388-170">La llamada a la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método envía un mensaje secundario para el usuario.</span><span class="sxs-lookup"><span data-stu-id="3e388-170">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="3e388-171">Esta llamada se realiza después de llamar a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devuelve `true` y si el `Force` parámetro no se estableció en `true`.</span><span class="sxs-lookup"><span data-stu-id="3e388-171">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="3e388-172">El usuario, a continuación, puede proporcionar comentarios para indicar si se debe continuar la operación.</span><span class="sxs-lookup"><span data-stu-id="3e388-172">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="3e388-173">Las llamadas de cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como una comprobación adicional para las modificaciones del sistema potencialmente peligroso o cuando desee proporcionar opciones sí a todo y no a todo al usuario.</span><span class="sxs-lookup"><span data-stu-id="3e388-173">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="3e388-174">El ejemplo siguiente muestra la llamada a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) de reemplazar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método en el ejemplo Cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3e388-174">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="3e388-175">Detener procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3e388-175">Stopping Input Processing</span></span>

<span data-ttu-id="3e388-176">El método de un cmdlet que realiza modificaciones en el sistema de procesamiento de entrada debe proporcionar una manera de detener el procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e388-176">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="3e388-177">En el caso de este cmdlet Stop-Proc, se realiza una llamada desde el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método a la [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) método.</span><span class="sxs-lookup"><span data-stu-id="3e388-177">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="3e388-178">Dado que el `PassThru` parámetro está establecido en `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) también llama a [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar el objeto de proceso a la canalización.</span><span class="sxs-lookup"><span data-stu-id="3e388-178">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3e388-179">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="3e388-179">Code Sample</span></span>

<span data-ttu-id="3e388-180">Para la completa C# código de ejemplo, vea [StopProcessSample01 ejemplo](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3e388-180">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="3e388-181">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="3e388-181">Defining Object Types and Formatting</span></span>

<span data-ttu-id="3e388-182">Windows PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="3e388-182">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="3e388-183">Por lo tanto, un cmdlet que deba definir su propio tipo o el cmdlet puede necesitar extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e388-183">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3e388-184">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="3e388-184">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3e388-185">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-185">Building the Cmdlet</span></span>

<span data-ttu-id="3e388-186">Después de implementar un cmdlet, se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e388-186">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3e388-187">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="3e388-187">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3e388-188">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-188">Testing the Cmdlet</span></span>

<span data-ttu-id="3e388-189">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="3e388-189">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3e388-190">Estas son varias pruebas que comprueban el cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3e388-190">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="3e388-191">Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3e388-191">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="3e388-192">Inicie Windows PowerShell y use el cmdlet Stop-Proc para detener el procesamiento, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="3e388-192">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="3e388-193">Dado que el cmdlet especifica la `Name` parámetro como obligatorios, las consultas de cmdlet para el parámetro.</span><span class="sxs-lookup"><span data-stu-id="3e388-193">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="3e388-194">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="3e388-194">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="3e388-195">Ahora vamos a usar el cmdlet para detener el proceso denominado "NOTEPAD".</span><span class="sxs-lookup"><span data-stu-id="3e388-195">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="3e388-196">El cmdlet le pide que confirme la acción.</span><span class="sxs-lookup"><span data-stu-id="3e388-196">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="3e388-197">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="3e388-197">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="3e388-198">Use Stop-Proc tal como se muestra para detener el proceso crítico denominado "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="3e388-198">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="3e388-199">Se le pida y advierte acerca de cómo realizar esta acción porque hará que el sistema operativo se reinicie.</span><span class="sxs-lookup"><span data-stu-id="3e388-199">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="3e388-200">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="3e388-200">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="3e388-201">Vamos a probar ahora detener el proceso WINLOGON sin recibir una advertencia.</span><span class="sxs-lookup"><span data-stu-id="3e388-201">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="3e388-202">Tenga en cuenta que esta entrada de comando utiliza el `Force` parámetro para invalidar la advertencia.</span><span class="sxs-lookup"><span data-stu-id="3e388-202">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="3e388-203">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="3e388-203">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="3e388-204">Véase también</span><span class="sxs-lookup"><span data-stu-id="3e388-204">See Also</span></span>

[<span data-ttu-id="3e388-205">Adición de parámetros que procesa la entrada de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="3e388-205">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3e388-206">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="3e388-206">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="3e388-207">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="3e388-207">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3e388-208">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3e388-208">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="3e388-209">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e388-209">Cmdlet Samples</span></span>](./cmdlet-samples.md)