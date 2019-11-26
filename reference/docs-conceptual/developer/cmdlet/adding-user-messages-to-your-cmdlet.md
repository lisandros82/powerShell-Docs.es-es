---
title: Agregando mensajes de usuario al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416030"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="290ff-102">Adición de mensajes de usuario al cmdlet</span><span class="sxs-lookup"><span data-stu-id="290ff-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="290ff-103">Los cmdlets pueden escribir varios tipos de mensajes que el tiempo de ejecución de Windows PowerShell puede mostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="290ff-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="290ff-104">Estos mensajes incluyen los siguientes tipos:</span><span class="sxs-lookup"><span data-stu-id="290ff-104">These messages include the following types:</span></span>

- <span data-ttu-id="290ff-105">Mensajes detallados que contienen información general del usuario.</span><span class="sxs-lookup"><span data-stu-id="290ff-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="290ff-106">Depure mensajes que contengan información de solución de problemas.</span><span class="sxs-lookup"><span data-stu-id="290ff-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="290ff-107">Mensajes de advertencia que contienen una notificación de que el cmdlet está a punto de realizar una operación que puede tener resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="290ff-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="290ff-108">Progreso de los mensajes de informe que contienen información sobre cuánto trabajo ha completado el cmdlet al realizar una operación que tarda mucho tiempo.</span><span class="sxs-lookup"><span data-stu-id="290ff-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="290ff-109">No hay ningún límite en cuanto al número de mensajes que el cmdlet puede escribir o el tipo de mensajes que escribe el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="290ff-110">Cada mensaje se escribe realizando una llamada específica desde el método de procesamiento de entrada del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="290ff-111">Definición del cmdlet</span><span class="sxs-lookup"><span data-stu-id="290ff-111">Defining the Cmdlet</span></span>

<span data-ttu-id="290ff-112">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="290ff-113">Cualquier tipo de cmdlet puede escribir notificaciones de usuario desde sus métodos de procesamiento de entrada; por lo tanto, en general, puede asignar un nombre a este cmdlet con cualquier verbo que indique qué modificaciones del sistema realiza el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="290ff-114">Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="290ff-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="290ff-115">El cmdlet Stop-proc está diseñado para modificar el sistema; por lo tanto, la declaración [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) de la clase .net debe incluir la palabra clave de atributo `SupportsShouldProcess` y establecerse en `true`.</span><span class="sxs-lookup"><span data-stu-id="290ff-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="290ff-116">El código siguiente es la definición de esta clase de cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="290ff-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="290ff-117">Para obtener más información acerca de esta definición, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="290ff-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="290ff-118">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="290ff-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="290ff-119">El cmdlet Stop-proc define tres parámetros: `Name`, `Force`y `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="290ff-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="290ff-120">Para obtener más información sobre cómo definir estos parámetros, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="290ff-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="290ff-121">Esta es la declaración de parámetro para el cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="290ff-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="290ff-122">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="290ff-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="290ff-123">El cmdlet debe invalidar un método de procesamiento de entrada. a menudo, será [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="290ff-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="290ff-124">Este cmdlet Stop-proc invalida el método de procesamiento de entrada [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="290ff-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="290ff-125">En esta implementación del cmdlet Stop-proc, se realizan llamadas para escribir mensajes detallados, mensajes de depuración y mensajes de advertencia.</span><span class="sxs-lookup"><span data-stu-id="290ff-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="290ff-126">Para obtener más información sobre cómo este método llama a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="290ff-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="290ff-127">Escribir un mensaje detallado</span><span class="sxs-lookup"><span data-stu-id="290ff-127">Writing a Verbose Message</span></span>

<span data-ttu-id="290ff-128">El método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) se usa para escribir información general de nivel de usuario que no está relacionada con condiciones de error específicas.</span><span class="sxs-lookup"><span data-stu-id="290ff-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="290ff-129">A continuación, el administrador del sistema puede usar esa información para continuar procesando otros comandos.</span><span class="sxs-lookup"><span data-stu-id="290ff-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="290ff-130">Además, toda la información escrita con este método debe localizarse según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="290ff-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="290ff-131">El siguiente código de este cmdlet Stop-proc muestra dos llamadas al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="290ff-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="290ff-132">Escribir un mensaje de depuración</span><span class="sxs-lookup"><span data-stu-id="290ff-132">Writing a Debug Message</span></span>

<span data-ttu-id="290ff-133">El método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) se usa para escribir mensajes de depuración que se pueden usar para solucionar problemas del funcionamiento del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="290ff-134">La llamada se realiza desde un método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="290ff-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="290ff-135">Windows PowerShell también define un parámetro `Debug` que presenta información detallada y de depuración.</span><span class="sxs-lookup"><span data-stu-id="290ff-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="290ff-136">Si el cmdlet admite este parámetro, no es necesario llamar a [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) en el mismo código que llama a [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="290ff-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="290ff-137">Las dos secciones siguientes del código del cmdlet Stop-proc de ejemplo muestran llamadas al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="290ff-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="290ff-138">Este mensaje de depuración se escribe inmediatamente antes de que se llame a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="290ff-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="290ff-139">Este mensaje de depuración se escribe inmediatamente antes de que se llame a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="290ff-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="290ff-140">Windows PowerShell enruta automáticamente cualquier llamada a [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) a la infraestructura de seguimiento y a los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="290ff-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="290ff-141">Esto permite realizar el seguimiento de las llamadas de método a la aplicación de hospedaje, a un archivo o a un depurador sin necesidad de realizar ningún trabajo de desarrollo adicional en el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="290ff-142">La entrada de línea de comandos siguiente implementa una operación de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="290ff-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="290ff-143">**PS > trace-Expression STOP-proc-File proc. log-comando STOP-proc Notepad**</span><span class="sxs-lookup"><span data-stu-id="290ff-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="290ff-144">Escribir un mensaje de advertencia</span><span class="sxs-lookup"><span data-stu-id="290ff-144">Writing a Warning Message</span></span>

<span data-ttu-id="290ff-145">El método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) se usa para escribir una advertencia cuando el cmdlet está a punto de realizar una operación que podría tener un resultado inesperado, por ejemplo, sobrescribir un archivo de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="290ff-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="290ff-146">El siguiente código del cmdlet Stop-proc de ejemplo muestra la llamada al método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) de la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="290ff-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="290ff-147">Escribir un mensaje de progreso</span><span class="sxs-lookup"><span data-stu-id="290ff-147">Writing a Progress Message</span></span>

<span data-ttu-id="290ff-148">[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) se usa para escribir mensajes de progreso cuando las operaciones de cmdlet tardan mucho tiempo en completarse.</span><span class="sxs-lookup"><span data-stu-id="290ff-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="290ff-149">Una llamada a [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) pasa un objeto [System. Management. Automation. Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) que se envía a la aplicación de hospedaje para su representación al usuario.</span><span class="sxs-lookup"><span data-stu-id="290ff-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="290ff-150">Este cmdlet Stop-proc no incluye una llamada al método [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .</span><span class="sxs-lookup"><span data-stu-id="290ff-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="290ff-151">El código siguiente es un ejemplo de un mensaje de progreso escrito por un cmdlet que está intentando copiar un elemento.</span><span class="sxs-lookup"><span data-stu-id="290ff-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="290ff-152">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="290ff-152">Code Sample</span></span>

<span data-ttu-id="290ff-153">Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample02](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="290ff-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="290ff-154">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="290ff-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="290ff-155">Windows PowerShell pasa información entre cmdlets mediante objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="290ff-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="290ff-156">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="290ff-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="290ff-157">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="290ff-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="290ff-158">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="290ff-158">Building the Cmdlet</span></span>

<span data-ttu-id="290ff-159">Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="290ff-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="290ff-160">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="290ff-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="290ff-161">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="290ff-161">Testing the Cmdlet</span></span>

<span data-ttu-id="290ff-162">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="290ff-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="290ff-163">Vamos a probar el cmdlet Stop-proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="290ff-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="290ff-164">Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="290ff-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="290ff-165">La siguiente entrada de línea de comandos usa STOP-proc para detener el proceso denominado "Bloc de notas", proporcionar notificaciones detalladas e imprimir información de depuración.</span><span class="sxs-lookup"><span data-stu-id="290ff-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="290ff-166">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="290ff-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="290ff-167">Vea también</span><span class="sxs-lookup"><span data-stu-id="290ff-167">See Also</span></span>

[<span data-ttu-id="290ff-168">Crear un cmdlet que modifique el sistema</span><span class="sxs-lookup"><span data-stu-id="290ff-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="290ff-169">Cómo crear un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="290ff-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="290ff-170">[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="290ff-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="290ff-171">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="290ff-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="290ff-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="290ff-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
