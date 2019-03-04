---
title: Adición de parámetros que procesan la entrada de línea de comandos | Microsoft Docs
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
ms.openlocfilehash: e010e28ec705932063bb418b260a1087fc3eef9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856011"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="4f910-102">Adición de parámetros que procesan la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="4f910-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="4f910-103">Un origen de entrada para un cmdlet es la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4f910-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="4f910-104">En este tema se describe cómo agregar un parámetro a la **Get-Proc** cmdlet (que se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet puede procesar la entrada desde el equipo local basado en explícito los objetos pasan al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="4f910-105">El **Get-Proc** cmdlet descrito aquí recupera los procesos basados en sus nombres y, a continuación, muestra información acerca de los procesos en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="4f910-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="4f910-106">Las secciones siguientes se encuentran en este tema:</span><span class="sxs-lookup"><span data-stu-id="4f910-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="4f910-107">Definición de la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="4f910-108">Declarar parámetros</span><span class="sxs-lookup"><span data-stu-id="4f910-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="4f910-109">Compatibilidad con la validación de parámetros</span><span class="sxs-lookup"><span data-stu-id="4f910-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="4f910-110">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="4f910-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="4f910-111">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="4f910-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="4f910-112">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="4f910-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="4f910-113">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="4f910-114">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="4f910-115">Definición de la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="4f910-116">El primer paso en la creación de cmdlet es la declaración de la clase de .NET Framework que implementa el cmdlet y nombres de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="4f910-117">Este cmdlet recupera información de proceso, por lo que el nombre del verbo seleccionado aquí es "Get".</span><span class="sxs-lookup"><span data-stu-id="4f910-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="4f910-118">(Casi cualquier tipo de cmdlet que es capaz de recuperar la información puede procesar la entrada de línea de comandos). Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="4f910-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="4f910-119">Esta es la declaración de clase para el **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="4f910-120">Se proporcionan detalles sobre esta definición en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4f910-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="4f910-121">Declarar parámetros</span><span class="sxs-lookup"><span data-stu-id="4f910-121">Declaring Parameters</span></span>

<span data-ttu-id="4f910-122">Un parámetro de cmdlet permite al usuario proporcionar la entrada al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="4f910-123">En el ejemplo siguiente, **Get-Proc** y `Get-Member` son los nombres de los cmdlets de canalizadas y `MemberType` es un parámetro para el `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="4f910-124">El parámetro tiene el argumento "property".</span><span class="sxs-lookup"><span data-stu-id="4f910-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="4f910-125">**PS > get-proc; `get-member` propiedad membertype:**</span><span class="sxs-lookup"><span data-stu-id="4f910-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="4f910-126">Para declarar parámetros para un cmdlet, primero debe definir las propiedades que representan los parámetros.</span><span class="sxs-lookup"><span data-stu-id="4f910-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="4f910-127">En el **Get-Proc** es el único parámetro de cmdlet, `Name`, en este caso, que representa el nombre del objeto de proceso de .NET Framework para recuperar.</span><span class="sxs-lookup"><span data-stu-id="4f910-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="4f910-128">Por lo tanto, la clase del cmdlet define una propiedad de tipo string para aceptar una matriz de nombres.</span><span class="sxs-lookup"><span data-stu-id="4f910-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="4f910-129">Esta es la declaración de parámetros para el `Name` parámetro de la **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="4f910-130">Informar al runtime de Windows PowerShell que esta propiedad es el `Name` parámetro, un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo se agrega a la definición de propiedad.</span><span class="sxs-lookup"><span data-stu-id="4f910-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="4f910-131">La sintaxis básica para declarar este atributo es `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="4f910-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="4f910-132">Un parámetro debe marcarse explícitamente como público.</span><span class="sxs-lookup"><span data-stu-id="4f910-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="4f910-133">Parámetros que no están marcados como público predeterminado para interno y no se encuentran el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f910-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="4f910-134">Este cmdlet usa una matriz de cadenas para el `Name` parámetro.</span><span class="sxs-lookup"><span data-stu-id="4f910-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="4f910-135">Si es posible, el cmdlet también debe definir un parámetro como una matriz, ya que esto permite al cmdlet que acepte más de un elemento.</span><span class="sxs-lookup"><span data-stu-id="4f910-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="4f910-136">Cosas que recordar acerca de las definiciones de parámetro</span><span class="sxs-lookup"><span data-stu-id="4f910-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="4f910-137">Se deben utilizar predefinidos Windows PowerShell parámetro nombres y tipos de datos tanto como sea posible para asegurarse de que el cmdlet es compatible con los cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f910-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="4f910-138">Por ejemplo, si todos los cmdlets usan predefinido `Id` nombre de parámetro para identificar un recurso, el usuario tendrá fácilmente entender el significado del parámetro, independientemente de qué cmdlet usan.</span><span class="sxs-lookup"><span data-stu-id="4f910-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="4f910-139">Básicamente, los nombres de parámetro siguen las mismas reglas que los usados para los nombres de variable en common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4f910-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="4f910-140">Para obtener más información sobre la nomenclatura de parámetros, vea [los nombres de parámetro de Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="4f910-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="4f910-141">Windows PowerShell se reserva algunos nombres de parámetro para proporcionar una experiencia de usuario coherente.</span><span class="sxs-lookup"><span data-stu-id="4f910-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="4f910-142">No use estos nombres de parámetro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, y `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4f910-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="4f910-143">Además, se reservan los siguientes alias para estos nombres de parámetro: `vb`, `db`, `ea`, `ev`, `ov`, y `ob`.</span><span class="sxs-lookup"><span data-stu-id="4f910-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="4f910-144">`Name` es un nombre de parámetro simples y común, recomendado para su uso en sus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4f910-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="4f910-145">Es mejor elegir un nombre de parámetro, así que un nombre complejo que es difícil de recordar y único para un cmdlet específico.</span><span class="sxs-lookup"><span data-stu-id="4f910-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="4f910-146">Los parámetros distinguen mayúsculas de minúsculas en Windows PowerShell, aunque de forma predeterminada el shell mantiene las mayúsculas.</span><span class="sxs-lookup"><span data-stu-id="4f910-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="4f910-147">Diferenciación de los argumentos depende de la operación del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="4f910-148">Argumentos se pasan a un parámetro, tal como se especifica en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4f910-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="4f910-149">Para obtener ejemplos de otras declaraciones de parámetros, vea [parámetros de Cmdlet](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4f910-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="4f910-150">Declarar parámetros como posicional o con nombre</span><span class="sxs-lookup"><span data-stu-id="4f910-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="4f910-151">Un cmdlet debe establecer cada parámetro como un parámetro posicional o con nombre.</span><span class="sxs-lookup"><span data-stu-id="4f910-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="4f910-152">Ambos tipos de parámetros aceptan argumentos únicos, varios argumentos separados por comas y valores booleanos.</span><span class="sxs-lookup"><span data-stu-id="4f910-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="4f910-153">Un parámetro booleano, también se denomina un *cambiar*, controla sólo la configuración del tipo Boolean.</span><span class="sxs-lookup"><span data-stu-id="4f910-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="4f910-154">El modificador se usa para determinar la presencia del parámetro.</span><span class="sxs-lookup"><span data-stu-id="4f910-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="4f910-155">El valor predeterminado recomendado es `false`.</span><span class="sxs-lookup"><span data-stu-id="4f910-155">The recommended default is `false`.</span></span>

<span data-ttu-id="4f910-156">El ejemplo **Get-Proc** cmdlet define el `Name` parámetro como un parámetro de posición por la posición 0.</span><span class="sxs-lookup"><span data-stu-id="4f910-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="4f910-157">Esto significa que el primer argumento que el usuario escribe en la línea de comandos se inserta automáticamente para este parámetro.</span><span class="sxs-lookup"><span data-stu-id="4f910-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="4f910-158">Si desea definir un parámetro con nombre, para que el usuario debe especificar el nombre del parámetro de la línea de comandos, deje el `Position` palabra clave fuera de la declaración de atributo.</span><span class="sxs-lookup"><span data-stu-id="4f910-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="4f910-159">A menos que los parámetros deben tener un nombre, se recomienda que use los parámetros usados más posicionales para que los usuarios no tendrán que escribir el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="4f910-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="4f910-160">Declarar parámetros como obligatorio u opcional</span><span class="sxs-lookup"><span data-stu-id="4f910-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="4f910-161">Un cmdlet debe establecer cada parámetro como opcional o un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="4f910-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="4f910-162">En el ejemplo **Get-Proc** cmdlet, el `Name` parámetro se define como opcional, porque el `Mandatory` palabra clave no está establecida en la declaración de atributo.</span><span class="sxs-lookup"><span data-stu-id="4f910-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="4f910-163">Compatibilidad con la validación de parámetros</span><span class="sxs-lookup"><span data-stu-id="4f910-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="4f910-164">El ejemplo **Get-Proc** cmdlet agrega un atributo de validación de entrada, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), a la `Name` parámetro para habilitar la validación que el entrada no es ni `null` ni está vacío.</span><span class="sxs-lookup"><span data-stu-id="4f910-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="4f910-165">Este atributo es uno de varios atributos de validación proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f910-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="4f910-166">Para obtener ejemplos de otros atributos de validación, consulte [validar entrada de parámetros](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="4f910-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="4f910-167">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="4f910-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="4f910-168">Si es su cmdlet controlar la entrada de línea de comandos, debe invalidar los métodos de procesamiento de entrada adecuada.</span><span class="sxs-lookup"><span data-stu-id="4f910-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="4f910-169">Los métodos de procesamiento de entrada básico se introducen en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4f910-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="4f910-170">El **Get-Proc** cmdlet reemplaza el [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para controlar el `Name` proporcionado por el usuario o un script de entrada de parámetros.</span><span class="sxs-lookup"><span data-stu-id="4f910-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="4f910-171">Este método obtiene los procesos para cada nombre de proceso solicitado, o todos los procesos si no se proporciona ningún nombre.</span><span class="sxs-lookup"><span data-stu-id="4f910-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="4f910-172">Tenga en cuenta que en [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) es el resultado mecanismo para enviar el resultado de los objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="4f910-172">Notice that in [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="4f910-173">El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` informar al runtime de Windows PowerShell para enumerar la matriz de salida de objetos de proceso y escribir un proceso a la vez en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4f910-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="4f910-174">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="4f910-174">Code Sample</span></span>

<span data-ttu-id="4f910-175">Para la completa C# código de ejemplo, vea [ejemplo GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4f910-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="4f910-176">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="4f910-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="4f910-177">Windows PowerShell pasa información entre los cmdlets de mediante el uso de objetos de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f910-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="4f910-178">Por lo tanto, podría necesitar un cmdlet definir su propio tipo, o un cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f910-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="4f910-179">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="4f910-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="4f910-180">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-180">Building the Cmdlet</span></span>

<span data-ttu-id="4f910-181">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell mediante el uso de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f910-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4f910-182">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="4f910-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4f910-183">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-183">Testing the Cmdlet</span></span>

<span data-ttu-id="4f910-184">Cuando el cmdlet se registra con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4f910-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="4f910-185">Hay dos formas para probar el código para el cmdlet de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="4f910-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="4f910-186">Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4f910-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="4f910-187">En el símbolo del sistema de Windows PowerShell, use el siguiente comando para enumerar el proceso de Internet Explorer, que se denomina "IEXPLORE."</span><span class="sxs-lookup"><span data-stu-id="4f910-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="4f910-188">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="4f910-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="4f910-189">Para enumerar los procesos de Internet Explorer, Outlook y el Bloc de notas denominados "IEXPLORE", "OUTLOOK" y "NOTEPAD", usan el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="4f910-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="4f910-190">Si hay varios procesos, todos ellos se muestran.</span><span class="sxs-lookup"><span data-stu-id="4f910-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="4f910-191">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="4f910-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="4f910-192">Véase también</span><span class="sxs-lookup"><span data-stu-id="4f910-192">See Also</span></span>

[<span data-ttu-id="4f910-193">Agregar parámetros de entrada de la canalización de proceso</span><span class="sxs-lookup"><span data-stu-id="4f910-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="4f910-194">Creación del primer Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="4f910-195">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="4f910-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="4f910-196">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="4f910-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="4f910-197">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f910-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="4f910-198">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f910-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
