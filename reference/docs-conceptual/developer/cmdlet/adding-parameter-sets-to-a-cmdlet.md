---
title: Agregar conjuntos de parámetros a un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416312"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="b218c-102">Adición de conjuntos de parámetros a un cmdlet</span><span class="sxs-lookup"><span data-stu-id="b218c-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="b218c-103">Aspectos que se deben conocer acerca de los conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="b218c-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="b218c-104">Windows PowerShell define un conjunto de parámetros como un grupo de parámetros que operan juntos.</span><span class="sxs-lookup"><span data-stu-id="b218c-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="b218c-105">Mediante la agrupación de los parámetros de un cmdlet, puede crear un cmdlet único que pueda cambiar su funcionalidad en función del grupo de parámetros que especifique el usuario.</span><span class="sxs-lookup"><span data-stu-id="b218c-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="b218c-106">Un ejemplo de un cmdlet que usa dos conjuntos de parámetros para definir funcionalidades diferentes es el cmdlet `Get-EventLog` proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b218c-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="b218c-107">Este cmdlet devuelve información diferente cuando el usuario especifica el parámetro `List` o `LogName`.</span><span class="sxs-lookup"><span data-stu-id="b218c-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="b218c-108">Si se especifica el parámetro `LogName`, el cmdlet devuelve información sobre los eventos de un registro de eventos determinado.</span><span class="sxs-lookup"><span data-stu-id="b218c-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="b218c-109">Si se especifica el parámetro `List`, el cmdlet devuelve información sobre los propios archivos de registro (no la información de evento que contienen).</span><span class="sxs-lookup"><span data-stu-id="b218c-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="b218c-110">En este caso, los parámetros `List` y `LogName` identifican dos conjuntos de parámetros independientes.</span><span class="sxs-lookup"><span data-stu-id="b218c-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="b218c-111">Dos aspectos importantes que hay que recordar sobre los conjuntos de parámetros es que el tiempo de ejecución de Windows PowerShell solo usa un conjunto de parámetros para una entrada determinada, y que cada conjunto de parámetros debe tener al menos un parámetro que sea único para ese conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="b218c-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="b218c-112">Para ilustrar ese último punto, este cmdlet Stop-proc usa tres conjuntos de parámetros: `ProcessName`, `ProcessId`y `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="b218c-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="b218c-113">Cada uno de estos conjuntos de parámetros tiene un parámetro que no está en los otros conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="b218c-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="b218c-114">Los conjuntos de parámetros podrían compartir otros parámetros, pero el cmdlet usa los parámetros únicos `ProcessName`, `ProcessId`y `InputObject` para identificar qué conjunto de parámetros debe usar el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b218c-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="b218c-115">Declarar la clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="b218c-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="b218c-116">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b218c-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b218c-117">Para este cmdlet, se usa el verbo de ciclo de vida "STOP" porque el cmdlet detiene los procesos del sistema.</span><span class="sxs-lookup"><span data-stu-id="b218c-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="b218c-118">El nombre de sustantivo "proc" se usa porque el cmdlet funciona en procesos.</span><span class="sxs-lookup"><span data-stu-id="b218c-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="b218c-119">En la declaración siguiente, tenga en cuenta que el verbo de cmdlet y el nombre de sustantivo se reflejan en el nombre de la clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b218c-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="b218c-120">Para obtener más información sobre los nombres de verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b218c-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b218c-121">El código siguiente es la definición de clase para este cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="b218c-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="b218c-122">Declarar los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="b218c-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="b218c-123">Este cmdlet define tres parámetros necesarios como entrada para el cmdlet (estos parámetros también definen los conjuntos de parámetros), así como un parámetro `Force` que administra lo que hace el cmdlet y un parámetro `PassThru` que determina si el cmdlet envía un objeto de salida a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="b218c-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="b218c-124">De forma predeterminada, este cmdlet no pasa un objeto a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="b218c-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="b218c-125">Para obtener más información sobre estos dos últimos parámetros, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b218c-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="b218c-126">Declarar el parámetro name</span><span class="sxs-lookup"><span data-stu-id="b218c-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="b218c-127">Este parámetro de entrada permite al usuario especificar los nombres de los procesos que se van a detener.</span><span class="sxs-lookup"><span data-stu-id="b218c-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="b218c-128">Tenga en cuenta que la palabra clave del atributo `ParameterSetName` del atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) especifica el conjunto de parámetros `ProcessName` para este parámetro.</span><span class="sxs-lookup"><span data-stu-id="b218c-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="b218c-129">Tenga en cuenta también que el alias "processName" se asigna a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="b218c-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="b218c-130">Declarar el parámetro id</span><span class="sxs-lookup"><span data-stu-id="b218c-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="b218c-131">Este parámetro de entrada permite al usuario especificar los identificadores de los procesos que se van a detener.</span><span class="sxs-lookup"><span data-stu-id="b218c-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="b218c-132">Tenga en cuenta que la palabra clave del atributo `ParameterSetName` del atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) especifica el conjunto de parámetros `ProcessId`.</span><span class="sxs-lookup"><span data-stu-id="b218c-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="b218c-133">Tenga en cuenta también que el alias "ProcessId" se asigna a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="b218c-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="b218c-134">Declarar el parámetro InputObject</span><span class="sxs-lookup"><span data-stu-id="b218c-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="b218c-135">Este parámetro de entrada permite al usuario especificar un objeto de entrada que contiene información sobre los procesos que se van a detener.</span><span class="sxs-lookup"><span data-stu-id="b218c-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="b218c-136">Tenga en cuenta que la palabra clave del atributo `ParameterSetName` del atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) especifica el conjunto de parámetros `InputObject` para este parámetro.</span><span class="sxs-lookup"><span data-stu-id="b218c-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="b218c-137">Tenga en cuenta también que este parámetro no tiene ningún alias.</span><span class="sxs-lookup"><span data-stu-id="b218c-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="b218c-138">Declarar parámetros en varios conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="b218c-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="b218c-139">Aunque debe haber un parámetro único para cada conjunto de parámetros, los parámetros pueden pertenecer a más de un conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="b218c-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="b218c-140">En estos casos, asigne al parámetro compartido una declaración de atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) para cada conjunto al que pertenece el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b218c-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="b218c-141">Si un parámetro está en todos los conjuntos de parámetros, solo tiene que declarar el atributo Parameter una vez y no es necesario especificar el nombre del conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="b218c-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b218c-142">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="b218c-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b218c-143">Cada cmdlet debe invalidar un método de procesamiento de entrada, lo que suele ser el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="b218c-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="b218c-144">En este cmdlet, el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) se invalida para que el cmdlet pueda procesar cualquier número de procesos.</span><span class="sxs-lookup"><span data-stu-id="b218c-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="b218c-145">Contiene una instrucción SELECT que llama a un método diferente en función del conjunto de parámetros especificado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b218c-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="b218c-146">Los métodos auxiliares a los que llama la instrucción SELECT no se describen aquí, pero puede ver su implementación en el ejemplo de código completo en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="b218c-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b218c-147">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="b218c-147">Code Sample</span></span>

<span data-ttu-id="b218c-148">Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b218c-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b218c-149">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="b218c-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b218c-150">Windows PowerShell pasa información entre cmdlets mediante objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="b218c-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b218c-151">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b218c-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b218c-152">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b218c-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b218c-153">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="b218c-153">Building the Cmdlet</span></span>

<span data-ttu-id="b218c-154">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b218c-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b218c-155">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b218c-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b218c-156">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="b218c-156">Testing the Cmdlet</span></span>

<span data-ttu-id="b218c-157">Cuando el cmdlet se haya registrado con Windows PowerShell, pruébelo en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="b218c-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="b218c-158">Estas son algunas pruebas que muestran cómo se pueden usar los parámetros `ProcessId` y `InputObject` para probar sus conjuntos de parámetros para detener un proceso.</span><span class="sxs-lookup"><span data-stu-id="b218c-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="b218c-159">Con Windows PowerShell iniciado, ejecute el cmdlet Stop-proc con el parámetro `ProcessId` establecido para detener un proceso en función de su identificador.</span><span class="sxs-lookup"><span data-stu-id="b218c-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="b218c-160">En este caso, el cmdlet usa el parámetro `ProcessId` establecido para detener el proceso.</span><span class="sxs-lookup"><span data-stu-id="b218c-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="b218c-161">Con Windows PowerShell iniciado, ejecute el cmdlet Stop-proc con el parámetro `InputObject` establecido para detener los procesos en el objeto de Bloc de notas recuperado por el comando `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="b218c-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="b218c-162">Véase también</span><span class="sxs-lookup"><span data-stu-id="b218c-162">See Also</span></span>

[<span data-ttu-id="b218c-163">Creación de un cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="b218c-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b218c-164">Cómo crear un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b218c-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="b218c-165">[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b218c-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="b218c-166">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b218c-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b218c-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b218c-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
