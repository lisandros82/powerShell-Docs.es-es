---
title: Agregar mensajes de usuario al Cmdlet | Microsoft Docs
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
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068783"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="3f87a-102">Adición de mensajes de usuario al cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="3f87a-103">Cmdlets puede escribir varios tipos de mensajes que se pueden mostrar al usuario el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f87a-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="3f87a-104">Estos mensajes incluyen los siguientes tipos:</span><span class="sxs-lookup"><span data-stu-id="3f87a-104">These messages include the following types:</span></span>

- <span data-ttu-id="3f87a-105">Mensajes detallados que contengan información general del usuario.</span><span class="sxs-lookup"><span data-stu-id="3f87a-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="3f87a-106">Los mensajes que contienen información de solución de problemas de depuración.</span><span class="sxs-lookup"><span data-stu-id="3f87a-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="3f87a-107">Los mensajes de advertencia que contienen una notificación de que el cmdlet que se va a realizar una operación que puede tener resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="3f87a-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="3f87a-108">Informe de progreso de los mensajes que contienen información sobre la cantidad funcionar el cmdlet se ha completado cuando se realiza una operación que tarda mucho tiempo.</span><span class="sxs-lookup"><span data-stu-id="3f87a-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="3f87a-109">No hay ningún límite al número de mensajes que puede escribir el cmdlet o el tipo de mensajes que el cmdlet escribe.</span><span class="sxs-lookup"><span data-stu-id="3f87a-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="3f87a-110">Cada mensaje se escribe mediante una llamada específica desde dentro de la entrada que procesar el método de su cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f87a-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="3f87a-111">El StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-111">The StopProc Cmdlet</span></span>

<span data-ttu-id="3f87a-112">Temas de esta sección incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3f87a-112">Topics in this section include the following:</span></span>

- [<span data-ttu-id="3f87a-113">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-113">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="3f87a-114">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="3f87a-114">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="3f87a-115">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3f87a-115">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="3f87a-116">Escribir un mensaje detallado</span><span class="sxs-lookup"><span data-stu-id="3f87a-116">Writing a Verbose Message</span></span>](#Writing-a-Verbose-Message)

- [<span data-ttu-id="3f87a-117">Escribir un mensaje de depuración</span><span class="sxs-lookup"><span data-stu-id="3f87a-117">Writing a Debug Message</span></span>](#Writing-a-Debug-Message)

- [<span data-ttu-id="3f87a-118">Escribir un mensaje de advertencia</span><span class="sxs-lookup"><span data-stu-id="3f87a-118">Writing a Warning Message</span></span>](#Writing-a-Warning-Message)

- [<span data-ttu-id="3f87a-119">Escribir un mensaje de progreso</span><span class="sxs-lookup"><span data-stu-id="3f87a-119">Writing a Progress Message</span></span>](#Writing-a-Progress-Message)

- [<span data-ttu-id="3f87a-120">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="3f87a-120">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="3f87a-121">Definir tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="3f87a-121">Define Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="3f87a-122">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-122">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="3f87a-123">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-123">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="3f87a-124">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-124">Defining the Cmdlet</span></span>

<span data-ttu-id="3f87a-125">El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f87a-125">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="3f87a-126">Cualquier tipo de cmdlet puede escribir las notificaciones de usuario desde su entrada de procesamiento de los métodos; en general, por lo tanto, puede asignar este cmdlet con cualquier verbo que indica qué modificaciones en el sistema realiza el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f87a-126">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="3f87a-127">Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3f87a-127">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3f87a-128">El cmdlet Stop-Proc está diseñado para modificar el sistema; por lo tanto, el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) debe incluir la declaración de la clase .NET del `SupportsShouldProcess` palabra clave de atributo y se puede establecer en `true`.</span><span class="sxs-lookup"><span data-stu-id="3f87a-128">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="3f87a-129">El código siguiente es la definición para esta clase de cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3f87a-129">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="3f87a-130">Para obtener más información acerca de esta definición, consulte [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="3f87a-130">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="3f87a-131">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="3f87a-131">Defining Parameters for System Modification</span></span>

<span data-ttu-id="3f87a-132">El cmdlet Stop-Proc define tres parámetros: `Name`, `Force`, y `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="3f87a-132">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="3f87a-133">Para obtener más información acerca de cómo definir estos parámetros, vea [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="3f87a-133">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="3f87a-134">Aquí es la declaración de parámetro para el cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="3f87a-134">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3f87a-135">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3f87a-135">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3f87a-136">El cmdlet debe invalidar una método de procesamiento de entrada, con más frecuencia será [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="3f87a-136">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="3f87a-137">Este cmdlet Stop-Proc invalida la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3f87a-137">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="3f87a-138">En esta implementación del cmdlet Stop-Proc, se realizan llamadas a escribir los mensajes detallados, mensajes de depuración y los mensajes de advertencia.</span><span class="sxs-lookup"><span data-stu-id="3f87a-138">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="3f87a-139">Para obtener más información acerca de cómo este método llama a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos, vea [Creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="3f87a-139">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="3f87a-140">Escribir un mensaje detallado</span><span class="sxs-lookup"><span data-stu-id="3f87a-140">Writing a Verbose Message</span></span>

<span data-ttu-id="3f87a-141">El [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método se utiliza para escribir información general de nivel de usuario que no está relacionado con las condiciones de error específico.</span><span class="sxs-lookup"><span data-stu-id="3f87a-141">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="3f87a-142">El administrador del sistema, a continuación, puede usar esa información para continuar procesando otros comandos.</span><span class="sxs-lookup"><span data-stu-id="3f87a-142">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="3f87a-143">Además, toda la información escrita con este método se debe traducir, según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="3f87a-143">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="3f87a-144">El siguiente código de este cmdlet Stop-Proc muestra dos llamadas a la [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método desde el reemplazo de la [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="3f87a-144">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="3f87a-145">Escribir un mensaje de depuración</span><span class="sxs-lookup"><span data-stu-id="3f87a-145">Writing a Debug Message</span></span>

<span data-ttu-id="3f87a-146">El [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método se utiliza para escribir mensajes de depuración que se pueden usar para solucionar problemas de funcionamiento del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f87a-146">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="3f87a-147">La llamada se realiza desde una método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3f87a-147">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="3f87a-148">Windows PowerShell también define un `Debug` parámetro que presenta ambos detallado y la información de depuración.</span><span class="sxs-lookup"><span data-stu-id="3f87a-148">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="3f87a-149">Si el cmdlet es compatible con este parámetro, no necesita llamar a [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) en el mismo código que llama a [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="3f87a-149">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="3f87a-150">Las dos secciones de código desde el cmdlet Stop-Proc de ejemplo siguientes muestran las llamadas a la [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método desde el reemplazo de la [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="3f87a-150">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="3f87a-151">Este mensaje de depuración se escribe inmediatamente antes de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) se llama.</span><span class="sxs-lookup"><span data-stu-id="3f87a-151">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="3f87a-152">Este mensaje de depuración se escribe inmediatamente antes de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) se llama.</span><span class="sxs-lookup"><span data-stu-id="3f87a-152">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="3f87a-153">Windows PowerShell se enruta automáticamente cualquier [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) las llamadas a los cmdlets y la infraestructura de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="3f87a-153">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="3f87a-154">Esto permite que las llamadas de método realizar un seguimiento a un depurador, un archivo o la aplicación de hospedaje sin tener que realizar ningún trabajo de desarrollo adicional en el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f87a-154">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="3f87a-155">La entrada de línea de comandos siguiente implementa una operación de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="3f87a-155">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="3f87a-156">**PS > Detener seguimiento-expression-proc-archivo proc.log-Bloc de notas de comando stop-proc**</span><span class="sxs-lookup"><span data-stu-id="3f87a-156">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="3f87a-157">Escribir un mensaje de advertencia</span><span class="sxs-lookup"><span data-stu-id="3f87a-157">Writing a Warning Message</span></span>

<span data-ttu-id="3f87a-158">El [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método se utiliza para escribir una advertencia cuando el cmdlet que se va a realizar una operación que podría tener un resultado inesperado, por ejemplo, sobrescribir un archivo de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="3f87a-158">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="3f87a-159">El siguiente código desde el cmdlet Stop-Proc de ejemplo muestra la llamada a la [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método desde el reemplazo de la [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="3f87a-159">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="3f87a-160">Escribir un mensaje de progreso</span><span class="sxs-lookup"><span data-stu-id="3f87a-160">Writing a Progress Message</span></span>

<span data-ttu-id="3f87a-161">El [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) se utiliza para escribir mensajes de progreso cuando las operaciones de cmdlet tienen un período prolongado de tiempo en completarse.</span><span class="sxs-lookup"><span data-stu-id="3f87a-161">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="3f87a-162">Una llamada a [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) pasa un [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objeto que se envía a la aplicación de hospedaje para representar al usuario.</span><span class="sxs-lookup"><span data-stu-id="3f87a-162">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="3f87a-163">Este cmdlet Stop-Proc no incluye una llamada a la [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.</span><span class="sxs-lookup"><span data-stu-id="3f87a-163">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="3f87a-164">El código siguiente es un ejemplo de un mensaje de progreso escrito por un cmdlet que está intentando copiar un elemento.</span><span class="sxs-lookup"><span data-stu-id="3f87a-164">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="3f87a-165">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="3f87a-165">Code Sample</span></span>

<span data-ttu-id="3f87a-166">Para la completa C# código de ejemplo, vea [StopProcessSample02 ejemplo](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3f87a-166">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="3f87a-167">Definir tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="3f87a-167">Define Object Types and Formatting</span></span>

<span data-ttu-id="3f87a-168">Windows PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="3f87a-168">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="3f87a-169">Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f87a-169">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3f87a-170">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="3f87a-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3f87a-171">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-171">Building the Cmdlet</span></span>

<span data-ttu-id="3f87a-172">Después de implementar un cmdlet, se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f87a-172">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3f87a-173">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="3f87a-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3f87a-174">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f87a-174">Testing the Cmdlet</span></span>

<span data-ttu-id="3f87a-175">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="3f87a-175">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3f87a-176">Vamos a probar el cmdlet Stop-Proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="3f87a-176">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="3f87a-177">Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3f87a-177">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="3f87a-178">La siguiente entrada de línea de comandos utiliza Stop-Proc para detener el proceso denominado "NOTEPAD", proporcionan notificaciones detalladas e imprimir la información de depuración.</span><span class="sxs-lookup"><span data-stu-id="3f87a-178">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="3f87a-179">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="3f87a-179">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3f87a-180">Véase también</span><span class="sxs-lookup"><span data-stu-id="3f87a-180">See Also</span></span>

[<span data-ttu-id="3f87a-181">Crear un Cmdlet que modifique el sistema</span><span class="sxs-lookup"><span data-stu-id="3f87a-181">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="3f87a-182">Creación de un Cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f87a-182">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="3f87a-183">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="3f87a-183">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="3f87a-184">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="3f87a-184">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3f87a-185">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3f87a-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
