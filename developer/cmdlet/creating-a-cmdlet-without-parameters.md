---
title: Creación de un Cmdlet sin parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860651"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="90e80-102">Creación de un cmdlet sin parámetros</span><span class="sxs-lookup"><span data-stu-id="90e80-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="90e80-103">En esta sección se describe cómo crear un cmdlet que recupera información desde el equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="90e80-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="90e80-104">El cmdlet que se describe aquí es un cmdlet Get-Proc que recupera información acerca de los procesos del equipo local y, a continuación, muestra esa información en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="90e80-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="90e80-105">Temas de esta sección incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="90e80-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="90e80-106">El Cmdlet de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="90e80-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="90e80-107">Definición de la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="90e80-108">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="90e80-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="90e80-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="90e80-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="90e80-110">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="90e80-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="90e80-111">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="90e80-112">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="90e80-113">Tenga en cuenta que, al escribir cmdlets, los ensamblados de referencia Windows PowerShell® se descargan en el disco (de forma predeterminada en C:\Program programa\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). No se instalan en la caché de ensamblados Global (GAC).</span><span class="sxs-lookup"><span data-stu-id="90e80-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="90e80-114">El Cmdlet de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="90e80-114">Naming the Cmdlet</span></span>

<span data-ttu-id="90e80-115">Un nombre de cmdlet consta de un verbo que indica que la acción que el cmdlet toma y un sustantivo que indica los elementos que actúa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="90e80-116">Dado que este cmdlet Get-Proc de ejemplo recupera los objetos de proceso, utiliza el verbo "Get", definido por el [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeración y el sustantivo "Proc" para indicar que el cmdlet funciona en elementos de proceso.</span><span class="sxs-lookup"><span data-stu-id="90e80-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="90e80-117">¿Al asignar nombres a los cmdlets, no utilice ninguno de los siguientes caracteres: #, () {} [] & - / \ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="90e80-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="90e80-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="90e80-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="90e80-119">Elegir un sustantivo</span><span class="sxs-lookup"><span data-stu-id="90e80-119">Choosing a Noun</span></span>

<span data-ttu-id="90e80-120">Debe elegir un sustantivo específico.</span><span class="sxs-lookup"><span data-stu-id="90e80-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="90e80-121">Es mejor usar un nombre singular precedido de una versión abreviada del nombre del producto.</span><span class="sxs-lookup"><span data-stu-id="90e80-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="90e80-122">Un nombre de cmdlet de ejemplo de este tipo es "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="90e80-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="90e80-123">Elección de un verbo</span><span class="sxs-lookup"><span data-stu-id="90e80-123">Choosing a Verb</span></span>

<span data-ttu-id="90e80-124">Debe usar un verbo del conjunto de los nombres de verbo del cmdlet aprobadas.</span><span class="sxs-lookup"><span data-stu-id="90e80-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="90e80-125">Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="90e80-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="90e80-126">Definición de la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="90e80-127">Una vez haya elegido un nombre de cmdlet, defina una clase .NET para implementar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="90e80-128">Esta es la definición de clase para este cmdlet Get-Proc de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="90e80-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="90e80-129">Tenga en cuenta que anteriores a la definición de clase, el [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo con la sintaxis `[Cmdlet(verb, noun, ...)]`, se usa para identificar esta clase como un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-129">Notice that previous to the class definition, the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="90e80-130">Este es el único atributo obligatorio para todos los cmdlets y permite el tiempo de ejecución de Windows PowerShell llamar correctamente a ellos.</span><span class="sxs-lookup"><span data-stu-id="90e80-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="90e80-131">Puede establecer las palabras clave de atributo para declarar aún más la clase si es necesario.</span><span class="sxs-lookup"><span data-stu-id="90e80-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="90e80-132">Tenga en cuenta que la declaración de atributos para la clase de ejemplo GetProcCommand declara sólo los nombres de sustantivo y el verbo del cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="90e80-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="90e80-133">Para todas las clases de atributo de Windows PowerShell, las palabras clave que se pueden establecer se corresponden con las propiedades de la clase de atributo.</span><span class="sxs-lookup"><span data-stu-id="90e80-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="90e80-134">Cuando asigne nombre a la clase del cmdlet, es una buena práctica para reflejar el nombre de cmdlet en el nombre de clase.</span><span class="sxs-lookup"><span data-stu-id="90e80-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="90e80-135">Para ello, use el formato "VerbNounCommand" y reemplace "Verbo" y "Sustantivo" con el verbo y sustantivo que se usa en el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="90e80-136">Como se muestra en la definición de clase anteriores, el cmdlet Get-Proc de ejemplo define una clase denominada GetProcCommand, que se deriva de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase base.</span><span class="sxs-lookup"><span data-stu-id="90e80-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90e80-137">Si desea definir un cmdlet que tiene acceso directo al tiempo de ejecución de Windows PowerShell, debe derivar la clase de .NET de la [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase base.</span><span class="sxs-lookup"><span data-stu-id="90e80-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="90e80-138">Para obtener más información acerca de esta clase, vea [creación de un Cmdlet que conjuntos de parámetros define](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="90e80-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="90e80-139">La clase para un cmdlet debe marcarse explícitamente como pública.</span><span class="sxs-lookup"><span data-stu-id="90e80-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="90e80-140">Las clases que no están marcadas como público predeterminado será interno y no se encontrará el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90e80-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="90e80-141">Windows PowerShell usa el [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) espacio de nombres para sus clases de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-141">Windows PowerShell uses the [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="90e80-142">Se recomienda colocar las clases de cmdlet en un espacio de nombres de comandos de su espacio de nombres de API, por ejemplo, xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="90e80-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="90e80-143">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="90e80-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="90e80-144">El [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase proporciona tres métodos de procesamiento de entrada principal, al menos uno de los cuales debe invalidar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="90e80-145">Para obtener más información acerca de cómo Windows PowerShell procesa los registros, vea [cómo Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="90e80-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="90e80-146">Para todos los tipos de entrada, el tiempo de ejecución de Windows PowerShell llama [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para habilitar el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="90e80-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="90e80-147">Si el cmdlet debe realizar algún preprocesamiento o programa de instalación, puede hacerlo mediante la invalidación de este método.</span><span class="sxs-lookup"><span data-stu-id="90e80-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="90e80-148">Windows PowerShell usa el término "registro" para describir el conjunto de valores de parámetro proporcionado cuando se llama a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="90e80-149">Si el cmdlet acepta entrada de la canalización, debe reemplazar el [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método y opcionalmente el [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)método.</span><span class="sxs-lookup"><span data-stu-id="90e80-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="90e80-150">Por ejemplo, un cmdlet podría reemplazar ambos métodos si lo recopila todos los datos de entrada mediante [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y, a continuación, opera en la entrada como un todo en lugar de un elemento a la vez, como el `Sort-Object` hace el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="90e80-151">Si el cmdlet no toma ninguna entrada de la canalización, debe invalidar el [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="90e80-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="90e80-152">Tenga en cuenta que este método se utiliza con frecuencia en lugar de [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cuando el cmdlet no puede funcionar en un elemento a la vez, como es el caso de un cmdlet de ordenación.</span><span class="sxs-lookup"><span data-stu-id="90e80-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="90e80-153">Dado que este cmdlet Get-Proc de ejemplo debe recibir la entrada de la canalización, invalida la [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método y utiliza las implementaciones predeterminadas para [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="90e80-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="90e80-154">El [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) invalidación recupera los procesos y los escribe en la línea de comandos mediante la [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método.</span><span class="sxs-lookup"><span data-stu-id="90e80-154">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="90e80-155">Cosas que recordar sobre el procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="90e80-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="90e80-156">El origen predeterminado para la entrada es un objeto explícito (por ejemplo, una cadena) proporcionado por el usuario en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="90e80-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="90e80-157">Para obtener más información, consulte [creación de un Cmdlet para entrada de línea de comandos del proceso](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="90e80-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="90e80-158">Una método de procesamiento de entrada también puede recibir entradas desde el objeto de salida de un cmdlet de nivel superior en la canalización.</span><span class="sxs-lookup"><span data-stu-id="90e80-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="90e80-159">Para obtener más información, consulte [creación de un Cmdlet para entrada de la canalización de proceso](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="90e80-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="90e80-160">Tenga en cuenta que el cmdlet puede recibir entradas de una combinación de línea de comandos y una canalización de orígenes.</span><span class="sxs-lookup"><span data-stu-id="90e80-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="90e80-161">El cmdlet de nivel inferior no puede devolver durante mucho tiempo o no en absoluto.</span><span class="sxs-lookup"><span data-stu-id="90e80-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="90e80-162">Por ese motivo, el método en el cmdlet de procesamiento de entrada no debe contener los bloqueos durante las llamadas a [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente los bloqueos para el que el ámbito se extiende más allá de la instancia del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90e80-163">Nunca debe llamar los cmdlets [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) o su equivalente.</span><span class="sxs-lookup"><span data-stu-id="90e80-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="90e80-164">El cmdlet podría tener las variables de objeto para limpiar cuando haya finalizado de procesamiento (por ejemplo, si se abre un identificador de archivo en el [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método y conserva el identificador se abra para su uso por [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="90e80-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="90e80-165">Es importante recordar que el tiempo de ejecución de Windows PowerShell no llame siempre a la [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método, que debe realizar la limpieza de objetos.</span><span class="sxs-lookup"><span data-stu-id="90e80-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="90e80-166">Por ejemplo, [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) no es posible que se llama si el cmdlet se cancela a medio camino o si un carácter de terminación se produce error en cualquier parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-166">For example, [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="90e80-167">Por lo tanto, un cmdlet que requiere la limpieza de objetos debe implementar toda [System.Idisposable](/dotnet/api/System.IDisposable) patrón, incluidos el finalizador, para que el tiempo de ejecución puede llamar a ambos [ System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) al final del procesamiento.</span><span class="sxs-lookup"><span data-stu-id="90e80-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="90e80-168">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="90e80-168">Code Sample</span></span>

<span data-ttu-id="90e80-169">Para la completa C# código de ejemplo, vea [ejemplo GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="90e80-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="90e80-170">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="90e80-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="90e80-171">Windows PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="90e80-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="90e80-172">Por lo tanto, un cmdlet es posible que deba definir su propio tipo o el cmdlet que tenga que ampliar un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90e80-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="90e80-173">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="90e80-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="90e80-174">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-174">Building the Cmdlet</span></span>

<span data-ttu-id="90e80-175">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90e80-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="90e80-176">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="90e80-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="90e80-177">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-177">Testing the Cmdlet</span></span>

<span data-ttu-id="90e80-178">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="90e80-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="90e80-179">El código para el cmdlet Get-Proc de ejemplo es pequeño, pero sigue usando el tiempo de ejecución de Windows PowerShell y un objeto .NET existente, que es suficiente para que resulte útil.</span><span class="sxs-lookup"><span data-stu-id="90e80-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="90e80-180">Vamos a probarlo para entender mejor lo que puede hacer Get-Proc y cómo se puede usar su salida.</span><span class="sxs-lookup"><span data-stu-id="90e80-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="90e80-181">Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="90e80-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="90e80-182">Inicie Windows PowerShell, y obtengan los procesos actuales que se ejecutan en el equipo.</span><span class="sxs-lookup"><span data-stu-id="90e80-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="90e80-183">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="90e80-184">Asignar una variable a los resultados del cmdlet para una manipulación más fácil.</span><span class="sxs-lookup"><span data-stu-id="90e80-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="90e80-185">Obtiene el número de procesos.</span><span class="sxs-lookup"><span data-stu-id="90e80-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="90e80-186">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="90e80-187">Recuperar un proceso específico.</span><span class="sxs-lookup"><span data-stu-id="90e80-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="90e80-188">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="90e80-189">Obtiene la hora de inicio de este proceso.</span><span class="sxs-lookup"><span data-stu-id="90e80-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="90e80-190">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="90e80-191">Obtener los procesos para el que el recuento de identificadores es mayor que 500 y clasificar el resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="90e80-192">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="90e80-193">Use el `Get-Member` cmdlet para enumerar las propiedades disponibles para cada proceso.</span><span class="sxs-lookup"><span data-stu-id="90e80-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="90e80-194">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="90e80-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="90e80-195">Véase también</span><span class="sxs-lookup"><span data-stu-id="90e80-195">See Also</span></span>

[<span data-ttu-id="90e80-196">Creación de un Cmdlet para procesar la entrada de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="90e80-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="90e80-197">Creación de un Cmdlet para procesar la entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="90e80-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="90e80-198">Creación de un Cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90e80-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="90e80-199">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="90e80-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="90e80-200">Cómo funciona Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90e80-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="90e80-201">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="90e80-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="90e80-202">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90e80-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="90e80-203">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="90e80-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)