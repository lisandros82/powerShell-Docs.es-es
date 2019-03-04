---
title: Adición de parámetro se establece en un Cmdlet | Microsoft Docs
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
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859271"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="32769-102">Adición de conjuntos de parámetros a un cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="32769-103">En esta sección se describe cómo agregar el parámetro se establece en el cmdlet Stop-Proc (se describe en [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="32769-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="32769-104">Al igual que los otros cmdlets de parada de proceso se describe en esta guía del programador, intentos de este cmdlet detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="32769-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="32769-105">Temas de esta sección incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="32769-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="32769-106">Cosas que saber acerca de conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="32769-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="32769-107">Declarar la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="32769-108">Declarar los parámetros del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="32769-109">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="32769-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="32769-110">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="32769-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="32769-111">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="32769-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="32769-112">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="32769-113">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="32769-114">Cosas que saber acerca de conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="32769-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="32769-115">Windows PowerShell define un parámetro establecido como un grupo de parámetros que operan conjuntamente.</span><span class="sxs-lookup"><span data-stu-id="32769-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="32769-116">Mediante la agrupación de los parámetros de un cmdlet, puede crear un solo cmdlet que puede cambiar su funcionalidad basada en el usuario especifica a qué grupo de parámetros.</span><span class="sxs-lookup"><span data-stu-id="32769-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="32769-117">Un ejemplo de un cmdlet que usa dos conjuntos de parámetros para definir distintas funcionalidades es la `Get-EventLog` cmdlet proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32769-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="32769-118">Este cmdlet devuelve información diferente cuando el usuario especifica la `List` o `LogName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="32769-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="32769-119">Si el `LogName` parámetro se especifica, el cmdlet devuelve información acerca de los eventos en un determinado registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="32769-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="32769-120">Si el `List` parámetro se especifica, el cmdlet devuelve información acerca del registro de archivos (no la información de evento que contienen).</span><span class="sxs-lookup"><span data-stu-id="32769-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="32769-121">En este caso, el `List` y `LogName` parámetros identifican dos conjuntos de parámetros independiente.</span><span class="sxs-lookup"><span data-stu-id="32769-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="32769-122">Dos aspectos importantes que recordar sobre los conjuntos de parámetros es que el tiempo de ejecución de Windows PowerShell usa un único conjunto de parámetros para una entrada determinada, y que cada conjunto de parámetros debe tener al menos un parámetro que es único para ese conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="32769-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="32769-123">Para ilustrar este último punto, este cmdlet Stop-Proc utiliza tres conjuntos de parámetros: `ProcessName`, `ProcessId`, y `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="32769-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="32769-124">Cada uno de estos conjuntos de parámetros tiene un parámetro que no está en los otros conjuntos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="32769-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="32769-125">Los conjuntos de parámetros podrían compartir otros parámetros, pero el cmdlet usa los parámetros únicos `ProcessName`, `ProcessId`, y `InputObject` para identificar qué conjunto de parámetros que debe usar el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32769-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="32769-126">Declarar la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="32769-127">El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32769-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="32769-128">Para este cmdlet, se utiliza el verbo de ciclo de vida "Stop" porque el cmdlet detiene los procesos del sistema.</span><span class="sxs-lookup"><span data-stu-id="32769-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="32769-129">Se usa el nombre de sustantivo "Proc" porque el cmdlet funciona en los procesos.</span><span class="sxs-lookup"><span data-stu-id="32769-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="32769-130">En la siguiente declaración, tenga en cuenta que el nombre del verbo y sustantivo cmdlet se reflejan en el nombre de la clase del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32769-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="32769-131">Para obtener más información acerca de los nombres de verbo del cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="32769-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="32769-132">El código siguiente es la definición de clase para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="32769-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="32769-133">Declarar los parámetros del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="32769-134">Este cmdlet define tres parámetros necesarios como entrada al cmdlet (estos parámetros también definen los conjuntos de parámetros), así como un `Force` parámetro que administra lo que hace el cmdlet y una `PassThru` parámetro que determina si el cmdlet envía un objeto de salida a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="32769-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="32769-135">De forma predeterminada, este cmdlet no pasa un objeto a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="32769-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="32769-136">Para obtener más información acerca de estos dos últimos parámetros, vea [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="32769-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="32769-137">Declarar el parámetro Name</span><span class="sxs-lookup"><span data-stu-id="32769-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="32769-138">Este parámetro de entrada permite al usuario especificar los nombres de los procesos que se va a detener.</span><span class="sxs-lookup"><span data-stu-id="32769-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="32769-139">Tenga en cuenta que el `ParameterSetName` atributo palabra clave de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica el `ProcessName` conjunto de parámetros para este parámetro.</span><span class="sxs-lookup"><span data-stu-id="32769-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="32769-140">Tenga en cuenta también que el alias "ProcessName" se asigna a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="32769-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="32769-141">Declarar el parámetro Id</span><span class="sxs-lookup"><span data-stu-id="32769-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="32769-142">Este parámetro de entrada permite al usuario especificar los identificadores de los procesos que se va a detener.</span><span class="sxs-lookup"><span data-stu-id="32769-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="32769-143">Tenga en cuenta que el `ParameterSetName` atributo palabra clave de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica el `ProcessId` conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="32769-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="32769-144">Tenga en cuenta también que el alias "ProcessId" se asigna a este parámetro.</span><span class="sxs-lookup"><span data-stu-id="32769-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="32769-145">Declarar el parámetro InputObject</span><span class="sxs-lookup"><span data-stu-id="32769-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="32769-146">Este parámetro de entrada permite al usuario especificar un objeto de entrada que contiene información sobre los procesos que se va a detener.</span><span class="sxs-lookup"><span data-stu-id="32769-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="32769-147">Tenga en cuenta que el `ParameterSetName` atributo palabra clave de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica el `InputObject` conjunto de parámetros para este parámetro.</span><span class="sxs-lookup"><span data-stu-id="32769-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="32769-148">Tenga en cuenta también que este parámetro no tiene ningún alias.</span><span class="sxs-lookup"><span data-stu-id="32769-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="32769-149">Declarar parámetros de varios conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="32769-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="32769-150">Aunque debe haber un parámetro único para cada conjunto de parámetros, los parámetros pueden pertenecer a más de un conjunto de parámetros.</span><span class="sxs-lookup"><span data-stu-id="32769-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="32769-151">En estos casos, asigne el parámetro compartido una [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaración de atributo para cada conjunto en los que el parámetro pertenece.</span><span class="sxs-lookup"><span data-stu-id="32769-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="32769-152">Si es un parámetro en todos los conjuntos de parámetros, solo tiene que declarar el atributo de parámetro de una vez y no es necesario especificar que el parámetro establece el nombre.</span><span class="sxs-lookup"><span data-stu-id="32769-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="32769-153">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="32769-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="32769-154">Todos los cmdlets deben invalidar una método de procesamiento de entrada, con más frecuencia esto será la [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="32769-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="32769-155">En este cmdlet, el [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método se reemplaza para que el cmdlet puede procesar cualquier número de procesos.</span><span class="sxs-lookup"><span data-stu-id="32769-155">In this cmdlet, the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="32769-156">Contiene una instrucción Select que llama a un método diferente basándose en qué conjunto de parámetros, el usuario ha especificado.</span><span class="sxs-lookup"><span data-stu-id="32769-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="32769-157">Los métodos auxiliares llamados por la instrucción Select no se describen aquí, pero puede ver su implementación en el ejemplo de código completo en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="32769-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="32769-158">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="32769-158">Code Sample</span></span>

<span data-ttu-id="32769-159">Para la completa C# código de ejemplo, vea [StopProcessSample04 ejemplo](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="32769-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="32769-160">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="32769-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="32769-161">Windows PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="32769-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="32769-162">Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32769-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="32769-163">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="32769-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="32769-164">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-164">Building the Cmdlet</span></span>

<span data-ttu-id="32769-165">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32769-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="32769-166">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="32769-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="32769-167">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32769-167">Testing the Cmdlet</span></span>

<span data-ttu-id="32769-168">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="32769-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="32769-169">Estas son algunas pruebas que demuestran cómo la `ProcessId` y `InputObject` parámetros se pueden usar para probar sus conjuntos de parámetros para detener un proceso.</span><span class="sxs-lookup"><span data-stu-id="32769-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="32769-170">Con Windows PowerShell iniciado, ejecute el cmdlet Stop-Proc con el `ProcessId` establecido para detener un proceso según su identificador.</span><span class="sxs-lookup"><span data-stu-id="32769-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="32769-171">En este caso, el cmdlet usa el `ProcessId` establecido para detener el proceso.</span><span class="sxs-lookup"><span data-stu-id="32769-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="32769-172">Con Windows PowerShell iniciado, ejecute el cmdlet Stop-Proc con el `InputObject` establecido para detener procesos en el objeto el Bloc de notas recuperado por el `Get-Process` comando.</span><span class="sxs-lookup"><span data-stu-id="32769-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="32769-173">Véase también</span><span class="sxs-lookup"><span data-stu-id="32769-173">See Also</span></span>

[<span data-ttu-id="32769-174">Creación de un Cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="32769-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="32769-175">Creación de un Cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="32769-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="32769-176">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="32769-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="32769-177">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="32769-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="32769-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="32769-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)