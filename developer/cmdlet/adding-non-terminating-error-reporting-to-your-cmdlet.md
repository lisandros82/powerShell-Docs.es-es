---
title: Agregar informes de errores para el Cmdlet de no terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068871"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="23c36-102">Adición de informes de errores de no terminación al cmdlet</span><span class="sxs-lookup"><span data-stu-id="23c36-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="23c36-103">Cmdlets puede notificar los errores de no terminación mediante una llamada a la [System.Management.Automation.Cmdlet.WriteError][] método y continuar funcionando en el objeto de entrada actual o en la entrada más objetos de canalización.</span><span class="sxs-lookup"><span data-stu-id="23c36-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="23c36-104">Esta sección explica cómo crear un cmdlet que informa de errores de no terminación de sus métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="23c36-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="23c36-105">Para errores de no terminación (así como los errores de terminación), el cmdlet debe pasar un [System.Management.Automation.ErrorRecord][] objeto que identifica el error.</span><span class="sxs-lookup"><span data-stu-id="23c36-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="23c36-106">Cada registro de error se identifica mediante una cadena única denominada "identificador de error".</span><span class="sxs-lookup"><span data-stu-id="23c36-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="23c36-107">Además, el identificador de la categoría de cada error se especifica mediante constantes definidas por un [System.Management.Automation.ErrorCategory][] enumeración.</span><span class="sxs-lookup"><span data-stu-id="23c36-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="23c36-108">El usuario puede ver los errores según su categoría estableciendo el `$ErrorView` variable a "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="23c36-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="23c36-109">Para obtener más información acerca de los registros de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="23c36-110">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="23c36-110">Defining the Cmdlet</span></span>

<span data-ttu-id="23c36-111">El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23c36-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="23c36-112">Este cmdlet recupera información de proceso, por lo que el nombre del verbo seleccionado aquí es "Get".</span><span class="sxs-lookup"><span data-stu-id="23c36-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="23c36-113">(Casi cualquier tipo de cmdlet que es capaz de recuperar la información puede procesar la entrada de línea de comandos). Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="23c36-114">La siguiente es la definición de este cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="23c36-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="23c36-115">Se proporcionan detalles de esta definición [crear su primer Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="23c36-116">Definición de parámetros</span><span class="sxs-lookup"><span data-stu-id="23c36-116">Defining Parameters</span></span>

<span data-ttu-id="23c36-117">Si es necesario, el cmdlet debe definir parámetros para el procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="23c36-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="23c36-118">Este cmdlet Get-Proc define un **nombre** parámetro tal y como se describe en [agregar parámetros que procesan datos de línea de comandos](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="23c36-119">Esta es la declaración de parámetros para el **nombre** parámetro de este cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="23c36-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="23c36-120">Invalidar los métodos de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="23c36-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="23c36-121">Debe invalidar todos los cmdlets de al menos uno de los métodos proporcionados por procesamiento de entrada la [System.Management.Automation.Cmdlet][] clase.</span><span class="sxs-lookup"><span data-stu-id="23c36-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="23c36-122">Estos métodos se describen en [crear su primer Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="23c36-123">El cmdlet debe controlar cada registro que de manera independiente como sea posible.</span><span class="sxs-lookup"><span data-stu-id="23c36-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="23c36-124">Este cmdlet Get-Proc invalida la [System.Management.Automation.Cmdlet.ProcessRecord][] método para controlar la **nombre** parámetro de entrada proporcionada por el usuario o una secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="23c36-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="23c36-125">Este método obtiene los procesos para cada nombre de proceso solicitado o todos los procesos si se proporciona ningún nombre.</span><span class="sxs-lookup"><span data-stu-id="23c36-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="23c36-126">Se proporcionan detalles de esta invalidación [crear su primer Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="23c36-127">Cosas que recordar al informar de errores</span><span class="sxs-lookup"><span data-stu-id="23c36-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="23c36-128">El [System.Management.Automation.ErrorRecord][] objeto que el cmdlet pasa al escribir un error requiere una excepción en su núcleo.</span><span class="sxs-lookup"><span data-stu-id="23c36-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="23c36-129">Siga las instrucciones de .NET al determinar la excepción a usar.</span><span class="sxs-lookup"><span data-stu-id="23c36-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="23c36-130">Básicamente, si el error semánticamente es igual que una excepción existente, debe usar el cmdlet o se derivan de esa excepción.</span><span class="sxs-lookup"><span data-stu-id="23c36-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="23c36-131">En caso contrario, debe derivar una nueva excepción o la jerarquía de excepciones directamente desde el [System.Exception][] clase.</span><span class="sxs-lookup"><span data-stu-id="23c36-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="23c36-132">Al crear identificadores de errores (que tiene accesibles a través de la propiedad FullyQualifiedErrorId de la clase ErrorRecord) tenga en cuenta lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="23c36-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="23c36-133">Utilice las cadenas que tienen como destino para fines de diagnóstico para que al inspeccionar el identificador completo puede determinar qué el error es y donde procede el error.</span><span class="sxs-lookup"><span data-stu-id="23c36-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="23c36-134">Un identificador de error completo con formato correcto podría ser como sigue.</span><span class="sxs-lookup"><span data-stu-id="23c36-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="23c36-135">Tenga en cuenta que en el ejemplo anterior, el identificador de error (el primer token) designa el error y la parte restante indica de dónde procede el error.</span><span class="sxs-lookup"><span data-stu-id="23c36-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="23c36-136">Para escenarios más complejos, el identificador de error puede ser un token de punto separado que se puede analizar de inspección.</span><span class="sxs-lookup"><span data-stu-id="23c36-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="23c36-137">Esto permite que bifurca demasiado en las partes del identificador del error, así como la categoría de error y el identificador de error.</span><span class="sxs-lookup"><span data-stu-id="23c36-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="23c36-138">El cmdlet debe asignar identificadores de error específico a diferentes rutas de código.</span><span class="sxs-lookup"><span data-stu-id="23c36-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="23c36-139">Tenga en cuenta para la asignación de identificadores de errores de la información siguiente:</span><span class="sxs-lookup"><span data-stu-id="23c36-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="23c36-140">Un identificador de error debe permanecer constante a lo largo del ciclo de vida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23c36-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="23c36-141">No se cambia la semántica de un identificador de error entre las versiones de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23c36-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="23c36-142">Use el texto para un identificador de error que lacónicamente corresponde a la que se informa del error.</span><span class="sxs-lookup"><span data-stu-id="23c36-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="23c36-143">No use signos de puntuación o espacios en blanco.</span><span class="sxs-lookup"><span data-stu-id="23c36-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="23c36-144">Tener su cmdlet generar identificadores de errores que son reproducibles.</span><span class="sxs-lookup"><span data-stu-id="23c36-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="23c36-145">Por ejemplo, no debe generar un identificador que incluye un identificador de proceso.</span><span class="sxs-lookup"><span data-stu-id="23c36-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="23c36-146">Los identificadores de error son útiles para un usuario solo cuando se corresponden con los identificadores que ven otros usuarios que experimentan el problema.</span><span class="sxs-lookup"><span data-stu-id="23c36-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="23c36-147">PowerShell no detecta las excepciones no controladas en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="23c36-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="23c36-148">Si un cmdlet crea un nuevo subproceso y el código que se ejecuta en ese subproceso produce una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.</span><span class="sxs-lookup"><span data-stu-id="23c36-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="23c36-149">Si un objeto tiene código en su destructor o los métodos Dispose que produce una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.</span><span class="sxs-lookup"><span data-stu-id="23c36-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="23c36-150">Informes de errores de no terminación</span><span class="sxs-lookup"><span data-stu-id="23c36-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="23c36-151">Uno de los métodos de procesamiento de entrada puede notificar un error de no terminación en el flujo de salida mediante la [System.Management.Automation.Cmdlet.WriteError][] método.</span><span class="sxs-lookup"><span data-stu-id="23c36-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="23c36-152">Este es un ejemplo de código de este cmdlet Get-Proc que ilustra la llamada a [System.Management.Automation.Cmdlet.WriteError][] desde dentro de la invalidación de la [System.Management.Automation.Cmdlet.ProcessRecord][] método.</span><span class="sxs-lookup"><span data-stu-id="23c36-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="23c36-153">En este caso, se realiza la llamada si el cmdlet no encuentra un proceso para un identificador de proceso especificado.</span><span class="sxs-lookup"><span data-stu-id="23c36-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="23c36-154">Cosas que recordar acerca de cómo escribir los errores de no terminación</span><span class="sxs-lookup"><span data-stu-id="23c36-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="23c36-155">Un error de no terminación, el cmdlet debe generar un identificador de error específico para cada objeto de entrada específico.</span><span class="sxs-lookup"><span data-stu-id="23c36-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="23c36-156">Con frecuencia necesita un cmdlet modificar la acción de PowerShell generada por un error de no terminación.</span><span class="sxs-lookup"><span data-stu-id="23c36-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="23c36-157">Puede hacerlo mediante la definición de la `ErrorAction` y `ErrorVariable` parámetros.</span><span class="sxs-lookup"><span data-stu-id="23c36-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="23c36-158">Si la definición de la `ErrorAction` parámetro, el cmdlet presenta las opciones de usuario [System.Management.Automation.ActionPreference][], directamente también pueden influir en la acción estableciendo el `$ErrorActionPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="23c36-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="23c36-159">El cmdlet puede guardar los errores de no terminación en una variable mediante el `ErrorVariable` parámetro, que no se ve afectado por el valor de `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="23c36-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="23c36-160">Errores se pueden anexar a una variable de error existente mediante la adición de un signo más (+) al principio del nombre de la variable.</span><span class="sxs-lookup"><span data-stu-id="23c36-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="23c36-161">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="23c36-161">Code Sample</span></span>

<span data-ttu-id="23c36-162">Para la completa C# código de ejemplo, vea [GetProcessSample04 ejemplo](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="23c36-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="23c36-163">Definir tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="23c36-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="23c36-164">PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="23c36-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="23c36-165">Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23c36-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="23c36-166">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="23c36-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="23c36-167">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="23c36-167">Building the Cmdlet</span></span>

<span data-ttu-id="23c36-168">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23c36-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="23c36-169">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="23c36-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="23c36-170">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="23c36-170">Testing the Cmdlet</span></span>

<span data-ttu-id="23c36-171">Cuando el cmdlet se ha registrado con PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="23c36-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="23c36-172">Vamos a probar el cmdlet Get-Proc de ejemplo para ver si notifica un error:</span><span class="sxs-lookup"><span data-stu-id="23c36-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="23c36-173">Inicie PowerShell y use el cmdlet Get-Proc para recuperar los procesos que se denomina "TEST".</span><span class="sxs-lookup"><span data-stu-id="23c36-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="23c36-174">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="23c36-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="23c36-175">Véase también</span><span class="sxs-lookup"><span data-stu-id="23c36-175">See Also</span></span>

[<span data-ttu-id="23c36-176">Agregar parámetros de entrada de la canalización de proceso</span><span class="sxs-lookup"><span data-stu-id="23c36-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="23c36-177">Adición de parámetros que procesa la entrada de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="23c36-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="23c36-178">Creación del primer Cmdlet</span><span class="sxs-lookup"><span data-stu-id="23c36-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="23c36-179">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="23c36-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="23c36-180">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="23c36-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="23c36-181">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23c36-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="23c36-182">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="23c36-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
