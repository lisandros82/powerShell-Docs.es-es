---
title: Agregar parámetros que procesan la entrada de línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322745"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="e550c-102">Adición de parámetros que procesan la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="e550c-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="e550c-103">Un origen de entrada para un cmdlet es la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e550c-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="e550c-104">En este tema se describe cómo agregar un parámetro al cmdlet **Get-proc** (que se describe en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet pueda procesar la entrada del equipo local en función de los objetos explícitos pasados al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e550c-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="e550c-105">El cmdlet **Get-proc** que se describe aquí recupera procesos en función de sus nombres y, a continuación, muestra información sobre los procesos en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="e550c-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="e550c-106">Definir la clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e550c-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="e550c-107">El primer paso en la creación de un cmdlet es la nomenclatura de los cmdlets y la declaración de la clase .NET Framework que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e550c-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="e550c-108">Este cmdlet recupera información de proceso, por lo que el nombre de verbo elegido aquí es "Get".</span><span class="sxs-lookup"><span data-stu-id="e550c-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="e550c-109">(Casi cualquier tipo de cmdlet que sea capaz de recuperar información puede procesar la entrada de la línea de comandos). Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e550c-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e550c-110">Esta es la declaración de clase para el cmdlet **Get-proc** .</span><span class="sxs-lookup"><span data-stu-id="e550c-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="e550c-111">En [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)se proporcionan detalles sobre esta definición.</span><span class="sxs-lookup"><span data-stu-id="e550c-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="e550c-112">Declarar parámetros</span><span class="sxs-lookup"><span data-stu-id="e550c-112">Declaring Parameters</span></span>

<span data-ttu-id="e550c-113">Un parámetro de cmdlet permite al usuario proporcionar entradas al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e550c-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="e550c-114">En el ejemplo siguiente, **Get-proc** y `Get-Member` son los nombres de los cmdlets canalizados y `MemberType` es un parámetro para el `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e550c-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="e550c-115">El parámetro tiene el argumento "Property".</span><span class="sxs-lookup"><span data-stu-id="e550c-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="e550c-116">**PS > Get-proc; `get-member` -MemberType (propiedad)**</span><span class="sxs-lookup"><span data-stu-id="e550c-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="e550c-117">Para declarar los parámetros de un cmdlet, primero debe definir las propiedades que representan los parámetros.</span><span class="sxs-lookup"><span data-stu-id="e550c-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="e550c-118">En el cmdlet **Get-proc** , el único parámetro es `Name`, que en este caso representa el nombre del objeto de proceso de .NET Framework que se va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="e550c-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="e550c-119">Por lo tanto, la clase de cmdlet define una propiedad de tipo cadena para aceptar una matriz de nombres.</span><span class="sxs-lookup"><span data-stu-id="e550c-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="e550c-120">Esta es la declaración de parámetro para `Name` el parámetro del cmdlet **Get-proc** .</span><span class="sxs-lookup"><span data-stu-id="e550c-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="e550c-121">Para notificar al tiempo de ejecución de Windows PowerShell que `Name` esta propiedad es el parámetro, se agrega un atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) a la definición de propiedad.</span><span class="sxs-lookup"><span data-stu-id="e550c-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="e550c-122">La sintaxis básica para declarar este atributo es `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="e550c-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="e550c-123">Un parámetro debe marcarse explícitamente como Public.</span><span class="sxs-lookup"><span data-stu-id="e550c-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="e550c-124">Los parámetros que no están marcados como públicos de forma predeterminada son internos y no se encuentran en el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e550c-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="e550c-125">Este cmdlet usa una matriz de cadenas para el `Name` parámetro.</span><span class="sxs-lookup"><span data-stu-id="e550c-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="e550c-126">Si es posible, el cmdlet también debe definir un parámetro como una matriz, ya que esto permite que el cmdlet acepte más de un elemento.</span><span class="sxs-lookup"><span data-stu-id="e550c-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="e550c-127">Aspectos que se deben recordar sobre las definiciones de parámetros</span><span class="sxs-lookup"><span data-stu-id="e550c-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="e550c-128">Los nombres de parámetros y tipos de datos predefinidos de Windows PowerShell deben reutilizarse lo máximo posible para asegurarse de que el cmdlet es compatible con los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e550c-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="e550c-129">Por ejemplo, si todos los cmdlets usan el nombre `Id` de parámetro predefinido para identificar un recurso, el usuario entenderá fácilmente el significado del parámetro, independientemente del cmdlet que estén usando.</span><span class="sxs-lookup"><span data-stu-id="e550c-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="e550c-130">Básicamente, los nombres de parámetro siguen las mismas reglas que los que se usan para los nombres de variable en el Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e550c-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="e550c-131">Para obtener más información sobre la nomenclatura de parámetros, consulte [nombres de parámetros de cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="e550c-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="e550c-132">Windows PowerShell reserva algunos nombres de parámetros para proporcionar una experiencia de usuario coherente.</span><span class="sxs-lookup"><span data-stu-id="e550c-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="e550c-133">No utilice estos nombres de parámetro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`y .`OutBuffer`</span><span class="sxs-lookup"><span data-stu-id="e550c-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="e550c-134">Además, se reservan los siguientes alias para los nombres de parámetro `vb`: `db`, `ea`, `ev`, `ov`, y `ob`.</span><span class="sxs-lookup"><span data-stu-id="e550c-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="e550c-135">`Name`es un nombre de parámetro simple y común, que se recomienda para su uso en los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e550c-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="e550c-136">Es mejor elegir un nombre de parámetro como este que un nombre complejo que sea único para un cmdlet específico y difícil de recordar.</span><span class="sxs-lookup"><span data-stu-id="e550c-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="e550c-137">Los parámetros no distinguen mayúsculas de minúsculas en Windows PowerShell, aunque de forma predeterminada el shell conserva el uso de mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e550c-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="e550c-138">La distinción de mayúsculas y minúsculas de los argumentos depende de la operación del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e550c-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="e550c-139">Los argumentos se pasan a un parámetro tal y como se especifica en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e550c-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="e550c-140">Para obtener ejemplos de otras declaraciones de parámetros, vea [parámetros de cmdlet](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e550c-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="e550c-141">Declarar parámetros como posicionales o con nombre</span><span class="sxs-lookup"><span data-stu-id="e550c-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="e550c-142">Un cmdlet debe establecer cada parámetro como un parámetro posicional o con nombre.</span><span class="sxs-lookup"><span data-stu-id="e550c-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="e550c-143">Ambos tipos de parámetros aceptan argumentos únicos, varios argumentos separados por comas y valores booleanos.</span><span class="sxs-lookup"><span data-stu-id="e550c-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="e550c-144">Un parámetro booleano, también denominado *modificador*, solo controla valores booleanos.</span><span class="sxs-lookup"><span data-stu-id="e550c-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="e550c-145">El modificador se usa para determinar la presencia del parámetro.</span><span class="sxs-lookup"><span data-stu-id="e550c-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="e550c-146">El valor predeterminado recomendado `false`es.</span><span class="sxs-lookup"><span data-stu-id="e550c-146">The recommended default is `false`.</span></span>

<span data-ttu-id="e550c-147">El cmdlet **Get-proc** de ejemplo define `Name` el parámetro como un parámetro posicional con la posición 0.</span><span class="sxs-lookup"><span data-stu-id="e550c-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="e550c-148">Esto significa que el primer argumento que el usuario escribe en la línea de comandos se inserta automáticamente para este parámetro.</span><span class="sxs-lookup"><span data-stu-id="e550c-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="e550c-149">Si desea definir un parámetro con nombre, para el que el usuario debe especificar el nombre del parámetro desde la línea de comandos, `Position` deje la palabra clave fuera de la declaración de atributo.</span><span class="sxs-lookup"><span data-stu-id="e550c-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="e550c-150">A menos que los parámetros se deban nombrar, se recomienda que haga que los parámetros más usados sean posicionales para que los usuarios no tengan que escribir el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="e550c-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="e550c-151">Declarar parámetros como obligatorios u opcionales</span><span class="sxs-lookup"><span data-stu-id="e550c-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="e550c-152">Un cmdlet debe establecer cada parámetro como parámetro opcional o obligatorio.</span><span class="sxs-lookup"><span data-stu-id="e550c-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="e550c-153">En el cmdlet **Get-proc** de ejemplo, `Name` el parámetro se define como opcional porque `Mandatory` la palabra clave no está establecida en la declaración de atributo.</span><span class="sxs-lookup"><span data-stu-id="e550c-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="e550c-154">Compatibilidad con la validación de parámetros</span><span class="sxs-lookup"><span data-stu-id="e550c-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="e550c-155">El cmdlet **Get-proc** de ejemplo agrega un atributo de validación de entrada, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute) `Name` , al parámetro para habilitar la `null` validación de que la entrada no es ni está vacía.</span><span class="sxs-lookup"><span data-stu-id="e550c-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="e550c-156">Este atributo es uno de varios atributos de validación proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e550c-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="e550c-157">Para obtener ejemplos de otros atributos de validación, vea [validar la entrada de parámetros](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="e550c-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e550c-158">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="e550c-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e550c-159">Si el cmdlet controla la entrada de la línea de comandos, debe invalidar los métodos de procesamiento de entrada adecuados.</span><span class="sxs-lookup"><span data-stu-id="e550c-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="e550c-160">Los métodos de procesamiento de entrada básicos se introducen en [crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e550c-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="e550c-161">El cmdlet **Get-proc** invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para controlar la `Name` entrada de parámetro proporcionada por el usuario o un script.</span><span class="sxs-lookup"><span data-stu-id="e550c-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="e550c-162">Este método obtiene los procesos para cada nombre de proceso solicitado, o todos para los procesos si no se proporciona ningún nombre.</span><span class="sxs-lookup"><span data-stu-id="e550c-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="e550c-163">Observe que en [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [System. Management. Automation. cmdlet. writeObject% 28System. Object% 2CSystem. Boolean% 29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) es el mecanismo de salida para enviar objetos de salida a la DUCCION.</span><span class="sxs-lookup"><span data-stu-id="e550c-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="e550c-164">El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` para informar al tiempo de ejecución de Windows PowerShell para enumerar la matriz de salida de los objetos de proceso y escribir un proceso cada vez en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e550c-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="e550c-165">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="e550c-165">Code Sample</span></span>

<span data-ttu-id="e550c-166">Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e550c-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="e550c-167">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="e550c-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="e550c-168">Windows PowerShell pasa información entre cmdlets mediante el uso de objetos de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e550c-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="e550c-169">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que un cmdlet necesite extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e550c-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e550c-170">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="e550c-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e550c-171">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="e550c-171">Building the Cmdlet</span></span>

<span data-ttu-id="e550c-172">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell mediante un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e550c-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e550c-173">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="e550c-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e550c-174">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="e550c-174">Testing the Cmdlet</span></span>

<span data-ttu-id="e550c-175">Cuando el cmdlet se registra con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e550c-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e550c-176">A continuación se muestran dos maneras de probar el código para el cmdlet de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e550c-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="e550c-177">Para obtener más información sobre el uso de cmdlets desde la línea de comandos, vea [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e550c-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="e550c-178">En el símbolo del sistema de Windows PowerShell, use el siguiente comando para mostrar el proceso de Internet Explorer, que se denomina "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="e550c-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="e550c-179">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="e550c-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="e550c-180">Para enumerar los procesos de Internet Explorer, Outlook y Notepad denominados "IEXPLORE", "OUTLOOK" y "NOTEPAD", use el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="e550c-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="e550c-181">Si hay varios procesos, se muestran todos ellos.</span><span class="sxs-lookup"><span data-stu-id="e550c-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="e550c-182">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="e550c-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="e550c-183">Vea también</span><span class="sxs-lookup"><span data-stu-id="e550c-183">See Also</span></span>

[<span data-ttu-id="e550c-184">Agregar parámetros que procesan la entrada de canalización</span><span class="sxs-lookup"><span data-stu-id="e550c-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="e550c-185">Creación del primer cmdlet</span><span class="sxs-lookup"><span data-stu-id="e550c-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="e550c-186">Extender tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="e550c-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="e550c-187">Cómo registrar cmdlets, proveedores y aplicaciones host</span><span class="sxs-lookup"><span data-stu-id="e550c-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e550c-188">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e550c-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e550c-189">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e550c-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
