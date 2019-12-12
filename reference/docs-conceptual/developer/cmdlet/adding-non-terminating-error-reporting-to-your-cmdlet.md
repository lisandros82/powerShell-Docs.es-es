---
title: Agregando informes de errores de no terminación al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364614"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="3fa24-102">Adición de informes de errores de no terminación al cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fa24-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="3fa24-103">Los cmdlets pueden notificar errores de no terminación llamando al método [System. Management. Automation. cmdlet. WriteError][] y continúan funcionando en el objeto de entrada actual o en objetos de canalización de entrada adicionales.</span><span class="sxs-lookup"><span data-stu-id="3fa24-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="3fa24-104">En esta sección se explica cómo crear un cmdlet que informe de errores de no terminación de sus métodos de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="3fa24-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="3fa24-105">En el caso de los errores de no terminación (así como de los errores de terminación), el cmdlet debe pasar un objeto [System. Management. Automation. ErrorRecord][] que identifique el error.</span><span class="sxs-lookup"><span data-stu-id="3fa24-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="3fa24-106">Cada registro de error se identifica mediante una cadena única denominada "identificador de error".</span><span class="sxs-lookup"><span data-stu-id="3fa24-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="3fa24-107">Además del identificador, la categoría de cada error se especifica mediante constantes definidas por una enumeración [System. Management. Automation. ErrorCategory][] .</span><span class="sxs-lookup"><span data-stu-id="3fa24-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="3fa24-108">El usuario puede ver los errores en función de su categoría estableciendo la variable de `$ErrorView` en "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="3fa24-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="3fa24-109">Para obtener más información sobre los registros de errores, consulte [registros de errores de Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="3fa24-110">Definición del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fa24-110">Defining the Cmdlet</span></span>

<span data-ttu-id="3fa24-111">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fa24-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="3fa24-112">Este cmdlet recupera información de proceso, por lo que el nombre de verbo elegido aquí es "Get".</span><span class="sxs-lookup"><span data-stu-id="3fa24-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="3fa24-113">(Casi cualquier tipo de cmdlet que sea capaz de recuperar información puede procesar la entrada de la línea de comandos). Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3fa24-114">A continuación se ofrece la definición de este cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="3fa24-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="3fa24-115">Los detalles de esta definición se proporcionan [al crear el primer cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="3fa24-116">Definición de parámetros</span><span class="sxs-lookup"><span data-stu-id="3fa24-116">Defining Parameters</span></span>

<span data-ttu-id="3fa24-117">Si es necesario, el cmdlet debe definir parámetros para procesar la entrada.</span><span class="sxs-lookup"><span data-stu-id="3fa24-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="3fa24-118">Este cmdlet Get-proc define un parámetro de **nombre** tal y como se describe en [agregar parámetros que procesan la entrada de la línea de comandos](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="3fa24-119">Esta es la declaración de parámetro para el parámetro **Name** de este cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="3fa24-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="3fa24-120">Reemplazar métodos de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="3fa24-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="3fa24-121">Todos los cmdlets deben invalidar al menos uno de los métodos de procesamiento de entrada proporcionados por la clase [System. Management. Automation. cmdlet][] .</span><span class="sxs-lookup"><span data-stu-id="3fa24-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="3fa24-122">Estos métodos se describen en [creación del primer cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3fa24-123">El cmdlet debe administrar cada registro de la forma más independiente posible.</span><span class="sxs-lookup"><span data-stu-id="3fa24-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="3fa24-124">Este cmdlet Get-proc invalida el método [System. Management. Automation. cmdlet. ProcessRecord][] para controlar el parámetro **Name** para la entrada proporcionada por el usuario o un script.</span><span class="sxs-lookup"><span data-stu-id="3fa24-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="3fa24-125">Este método obtendrá los procesos de cada nombre de proceso solicitado o de todos los procesos si no se proporciona ningún nombre.</span><span class="sxs-lookup"><span data-stu-id="3fa24-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="3fa24-126">Los detalles de esta invalidación se proporcionan [al crear el primer cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="3fa24-127">Aspectos que se deben recordar al informar de errores</span><span class="sxs-lookup"><span data-stu-id="3fa24-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="3fa24-128">El objeto [System. Management. Automation. ErrorRecord][] que el cmdlet pasa cuando se escribe un error requiere una excepción en su núcleo.</span><span class="sxs-lookup"><span data-stu-id="3fa24-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="3fa24-129">Siga las instrucciones de .NET para determinar la excepción que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="3fa24-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="3fa24-130">Básicamente, si el error es semánticamente igual que una excepción existente, el cmdlet debe usar o derivar de esa excepción.</span><span class="sxs-lookup"><span data-stu-id="3fa24-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="3fa24-131">De lo contrario, debe derivar una nueva jerarquía de excepción o excepción directamente de la clase [System. Exception][] .</span><span class="sxs-lookup"><span data-stu-id="3fa24-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="3fa24-132">Al crear identificadores de error (a los que se tiene acceso a través de la propiedad FullyQualifiedErrorId de la clase ErrorRecord) tenga en cuenta lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="3fa24-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="3fa24-133">Use cadenas destinadas a fines de diagnóstico para que, al inspeccionar el identificador completo, pueda determinar cuál es el error y dónde procede el error.</span><span class="sxs-lookup"><span data-stu-id="3fa24-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="3fa24-134">Un identificador de error completo bien formado puede ser como se indica A continuación.</span><span class="sxs-lookup"><span data-stu-id="3fa24-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="3fa24-135">Observe que en el ejemplo anterior, el identificador de error (el primer token) designa cuál es el error y la parte restante indica dónde procede el error.</span><span class="sxs-lookup"><span data-stu-id="3fa24-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="3fa24-136">En escenarios más complejos, el identificador de error puede ser un token separado por puntos que se puede analizar en la inspección.</span><span class="sxs-lookup"><span data-stu-id="3fa24-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="3fa24-137">Esto le permite crear una bifurcación en las partes del identificador de error, así como el identificador de error y la categoría de error.</span><span class="sxs-lookup"><span data-stu-id="3fa24-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="3fa24-138">El cmdlet debe asignar identificadores de error específicos a rutas de acceso de código diferentes.</span><span class="sxs-lookup"><span data-stu-id="3fa24-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="3fa24-139">Tenga en cuenta la siguiente información para la asignación de identificadores de error:</span><span class="sxs-lookup"><span data-stu-id="3fa24-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="3fa24-140">Un identificador de error debe permanecer constante en todo el ciclo de vida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fa24-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="3fa24-141">No cambie la semántica de un identificador de error entre las versiones de los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3fa24-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="3fa24-142">Use texto para un identificador de error que tersely corresponda con el error que se va a informar.</span><span class="sxs-lookup"><span data-stu-id="3fa24-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="3fa24-143">No utilice espacios en blanco ni signos de puntuación.</span><span class="sxs-lookup"><span data-stu-id="3fa24-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="3fa24-144">Haga que el cmdlet genere solo identificadores de error que se pueden reproducir.</span><span class="sxs-lookup"><span data-stu-id="3fa24-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="3fa24-145">Por ejemplo, no debe generar un identificador que incluya un identificador de proceso.</span><span class="sxs-lookup"><span data-stu-id="3fa24-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="3fa24-146">Los identificadores de error son útiles para un usuario solo cuando se corresponden con los identificadores que ven otros usuarios que experimentan el mismo problema.</span><span class="sxs-lookup"><span data-stu-id="3fa24-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="3fa24-147">PowerShell no detecta las excepciones no controladas en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="3fa24-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="3fa24-148">Si un cmdlet crea un nuevo subproceso y el código que se ejecuta en ese subproceso produce una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.</span><span class="sxs-lookup"><span data-stu-id="3fa24-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="3fa24-149">Si un objeto tiene código en su destructor o métodos Dispose que causan una excepción no controlada, PowerShell no detectará el error y finalizará el proceso.</span><span class="sxs-lookup"><span data-stu-id="3fa24-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="3fa24-150">Informes de errores de no terminación</span><span class="sxs-lookup"><span data-stu-id="3fa24-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="3fa24-151">Cualquiera de los métodos de procesamiento de entrada puede notificar un error de no terminación en el flujo de salida mediante el método [System. Management. Automation. cmdlet. WriteError][] .</span><span class="sxs-lookup"><span data-stu-id="3fa24-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="3fa24-152">Este es un ejemplo de código de este cmdlet Get-proc que ilustra la llamada a [System. Management. Automation. cmdlet. WriteError][] desde dentro de la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord][] .</span><span class="sxs-lookup"><span data-stu-id="3fa24-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="3fa24-153">En este caso, se realiza la llamada si el cmdlet no encuentra un proceso para un identificador de proceso especificado.</span><span class="sxs-lookup"><span data-stu-id="3fa24-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="3fa24-154">Aspectos que se deben recordar sobre la escritura de errores de no terminación</span><span class="sxs-lookup"><span data-stu-id="3fa24-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="3fa24-155">En el caso de un error de no terminación, el cmdlet debe generar un identificador de error específico para cada objeto de entrada concreto.</span><span class="sxs-lookup"><span data-stu-id="3fa24-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="3fa24-156">Con frecuencia, un cmdlet necesita modificar la acción de PowerShell generada por un error de no terminación.</span><span class="sxs-lookup"><span data-stu-id="3fa24-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="3fa24-157">Para ello, puede definir los parámetros `ErrorAction` y `ErrorVariable`.</span><span class="sxs-lookup"><span data-stu-id="3fa24-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="3fa24-158">Si define el parámetro `ErrorAction`, el cmdlet presenta las opciones de usuario [System. Management. Automation. ActionPreference][], también puede influir directamente en la acción estableciendo la variable `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="3fa24-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="3fa24-159">El cmdlet puede guardar errores de no terminación en una variable mediante el parámetro `ErrorVariable`, que no se ve afectado por la configuración de `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="3fa24-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="3fa24-160">Los errores se pueden anexar a una variable de error existente agregando un signo más (+) al principio del nombre de la variable.</span><span class="sxs-lookup"><span data-stu-id="3fa24-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3fa24-161">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="3fa24-161">Code Sample</span></span>

<span data-ttu-id="3fa24-162">Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample04](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3fa24-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="3fa24-163">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="3fa24-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="3fa24-164">PowerShell pasa información entre cmdlets mediante objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="3fa24-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="3fa24-165">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fa24-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="3fa24-166">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="3fa24-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3fa24-167">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fa24-167">Building the Cmdlet</span></span>

<span data-ttu-id="3fa24-168">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fa24-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="3fa24-169">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="3fa24-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3fa24-170">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fa24-170">Testing the Cmdlet</span></span>

<span data-ttu-id="3fa24-171">Cuando el cmdlet se ha registrado con PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="3fa24-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="3fa24-172">Vamos a probar el cmdlet Get-proc de ejemplo para ver si informa de un error:</span><span class="sxs-lookup"><span data-stu-id="3fa24-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="3fa24-173">Inicie PowerShell y use el cmdlet Get-proc para recuperar los procesos denominados "TEST".</span><span class="sxs-lookup"><span data-stu-id="3fa24-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="3fa24-174">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="3fa24-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="3fa24-175">Véase también</span><span class="sxs-lookup"><span data-stu-id="3fa24-175">See Also</span></span>

[<span data-ttu-id="3fa24-176">Agregar parámetros que procesan la entrada de canalización</span><span class="sxs-lookup"><span data-stu-id="3fa24-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="3fa24-177">Agregar parámetros que procesan la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="3fa24-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3fa24-178">Creación del primer cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fa24-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="3fa24-179">Extender tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="3fa24-179">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="3fa24-180">Cómo registrar cmdlets, proveedores y aplicaciones host</span><span class="sxs-lookup"><span data-stu-id="3fa24-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3fa24-181">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fa24-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="3fa24-182">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fa24-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[System. Management. Automation. ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
