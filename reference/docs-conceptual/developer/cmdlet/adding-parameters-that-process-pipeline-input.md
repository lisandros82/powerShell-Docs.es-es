---
title: Agregando parámetros que procesan la entrada de canalización | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364604"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="f0e63-102">Adición de parámetros que procesan la entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="f0e63-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="f0e63-103">Un origen de entrada para un cmdlet es un objeto de la canalización que se origina en un cmdlet de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="f0e63-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="f0e63-104">En esta sección se describe cómo agregar un parámetro al cmdlet Get-proc (descrito en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet pueda procesar objetos de canalización.</span><span class="sxs-lookup"><span data-stu-id="f0e63-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="f0e63-105">Este cmdlet Get-proc usa un parámetro `Name` que acepta la entrada de un objeto de canalización, recupera información del proceso del equipo local en función de los nombres proporcionados y, a continuación, muestra información sobre los procesos en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f0e63-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="f0e63-106">Definir la clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0e63-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="f0e63-107">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0e63-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="f0e63-108">Este cmdlet recupera información de proceso, por lo que el nombre de verbo elegido aquí es "Get".</span><span class="sxs-lookup"><span data-stu-id="f0e63-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="f0e63-109">(Casi cualquier tipo de cmdlet que sea capaz de recuperar información puede procesar la entrada de la línea de comandos). Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f0e63-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="f0e63-110">A continuación se ofrece la definición de este cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="f0e63-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="f0e63-111">Los detalles de esta definición se proporcionan [al crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f0e63-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="f0e63-112">Definir la entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="f0e63-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="f0e63-113">En esta sección se describe cómo definir la entrada desde la canalización para un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0e63-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="f0e63-114">Este cmdlet Get-proc define una propiedad que representa el parámetro `Name` tal y como se describe en [agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="f0e63-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="f0e63-115">(Vea ese tema para obtener información general sobre la declaración de parámetros).</span><span class="sxs-lookup"><span data-stu-id="f0e63-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="f0e63-116">Sin embargo, cuando un cmdlet necesita procesar la entrada de canalización, el tiempo de ejecución de Windows PowerShell debe enlazar sus parámetros a los valores de entrada.</span><span class="sxs-lookup"><span data-stu-id="f0e63-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="f0e63-117">Para ello, debe agregar la palabra clave `ValueFromPipeline` o agregar la palabra clave `ValueFromPipelineByProperty` a la declaración [del atributo System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f0e63-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="f0e63-118">Especifique la palabra clave `ValueFromPipeline` si el cmdlet tiene acceso al objeto de entrada completo.</span><span class="sxs-lookup"><span data-stu-id="f0e63-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="f0e63-119">Especifique el `ValueFromPipelineByProperty` si el cmdlet tiene acceso solo a una propiedad del objeto.</span><span class="sxs-lookup"><span data-stu-id="f0e63-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="f0e63-120">Esta es la declaración de parámetro para el parámetro `Name` de este cmdlet Get-proc que acepta la entrada de canalización.</span><span class="sxs-lookup"><span data-stu-id="f0e63-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="f0e63-121">La declaración anterior establece la palabra clave `ValueFromPipeline` en `true` para que el tiempo de ejecución de Windows PowerShell enlace el parámetro al objeto entrante si el objeto es del mismo tipo que el parámetro, o si se puede convertir en el mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="f0e63-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="f0e63-122">La palabra clave `ValueFromPipelineByPropertyName` también se establece en `true` para que el tiempo de ejecución de Windows PowerShell Compruebe el objeto de entrada de una propiedad `Name`.</span><span class="sxs-lookup"><span data-stu-id="f0e63-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="f0e63-123">Si el objeto entrante tiene este tipo de propiedad, el tiempo de ejecución enlazará el parámetro `Name` a la propiedad `Name` del objeto entrante.</span><span class="sxs-lookup"><span data-stu-id="f0e63-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="f0e63-124">La configuración de la palabra clave del atributo `ValueFromPipeline` para un parámetro tiene prioridad sobre la configuración de la palabra clave `ValueFromPipelineByPropertyName`.</span><span class="sxs-lookup"><span data-stu-id="f0e63-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f0e63-125">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="f0e63-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f0e63-126">Si el cmdlet controla la entrada de canalización, debe invalidar los métodos de procesamiento de entrada adecuados.</span><span class="sxs-lookup"><span data-stu-id="f0e63-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="f0e63-127">Los métodos de procesamiento de entrada básicos se introducen en [crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f0e63-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="f0e63-128">Este cmdlet Get-proc invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para controlar la entrada de parámetro `Name` proporcionada por el usuario o un script.</span><span class="sxs-lookup"><span data-stu-id="f0e63-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="f0e63-129">Este método obtendrá los procesos de cada nombre de proceso solicitado o de todos los procesos si no se proporciona ningún nombre.</span><span class="sxs-lookup"><span data-stu-id="f0e63-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="f0e63-130">Tenga en cuenta que en [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) es el mecanismo de salida para enviar objetos de salida a la canalización.</span><span class="sxs-lookup"><span data-stu-id="f0e63-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="f0e63-131">El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` para indicar al tiempo de ejecución de Windows PowerShell que Enumere la matriz de objetos de proceso y que escriba un proceso cada vez en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f0e63-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="f0e63-132">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="f0e63-132">Code Sample</span></span>

<span data-ttu-id="f0e63-133">Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f0e63-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="f0e63-134">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="f0e63-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="f0e63-135">Windows PowerShell pasa información entre cmdlets mediante objetos .net.</span><span class="sxs-lookup"><span data-stu-id="f0e63-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="f0e63-136">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0e63-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f0e63-137">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f0e63-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f0e63-138">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0e63-138">Building the Cmdlet</span></span>

<span data-ttu-id="f0e63-139">Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0e63-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f0e63-140">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f0e63-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f0e63-141">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0e63-141">Testing the Cmdlet</span></span>

<span data-ttu-id="f0e63-142">Cuando el cmdlet se haya registrado con Windows PowerShell, pruébelo en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f0e63-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="f0e63-143">Por ejemplo, pruebe el código para el cmdlet de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f0e63-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="f0e63-144">Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f0e63-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="f0e63-145">En el símbolo del sistema de Windows PowerShell, escriba los siguientes comandos para recuperar los nombres de los procesos a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="f0e63-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="f0e63-146">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="f0e63-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="f0e63-147">Escriba las líneas siguientes para obtener los objetos de proceso que tienen una propiedad `Name` de los procesos denominados "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="f0e63-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="f0e63-148">En este ejemplo se usa el cmdlet `Get-Process` (proporcionado por Windows PowerShell) como un comando de nivel superior para recuperar los procesos "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="f0e63-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="f0e63-149">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="f0e63-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="f0e63-150">Véase también</span><span class="sxs-lookup"><span data-stu-id="f0e63-150">See Also</span></span>

[<span data-ttu-id="f0e63-151">Agregar parámetros que procesan la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="f0e63-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f0e63-152">Creación del primer cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0e63-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="f0e63-153">[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f0e63-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="f0e63-154">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f0e63-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="f0e63-155">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0e63-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="f0e63-156">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0e63-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
