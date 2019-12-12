---
title: Crear un cmdlet sin parámetros | Microsoft Docs
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
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415673"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="daa9c-102">Creación de un cmdlet sin parámetros</span><span class="sxs-lookup"><span data-stu-id="daa9c-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="daa9c-103">En esta sección se describe cómo crear un cmdlet que recupera información del equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="daa9c-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="daa9c-104">El cmdlet descrito aquí es un cmdlet Get-proc que recupera información sobre los procesos del equipo local y, a continuación, muestra esa información en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="daa9c-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="daa9c-105">Tenga en cuenta que al escribir cmdlets, los ensamblados de referencia de® de Windows PowerShell se descargan en el disco (de forma predeterminada, en C:\Archivos de Programa\reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="daa9c-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="daa9c-106">No se instalan en la caché de ensamblados global (GAC).</span><span class="sxs-lookup"><span data-stu-id="daa9c-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="daa9c-107">Asignar nombre al cmdlet</span><span class="sxs-lookup"><span data-stu-id="daa9c-107">Naming the Cmdlet</span></span>

<span data-ttu-id="daa9c-108">Un nombre de cmdlet consta de un verbo que indica la acción que el cmdlet toma y un sustantivo que indica los elementos sobre los que actúa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="daa9c-109">Dado que este cmdlet Get-proc de ejemplo recupera objetos de proceso, usa el verbo "Get", definido por la enumeración [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) y el nombre "proc" para indicar que el cmdlet funciona en elementos de proceso.</span><span class="sxs-lookup"><span data-stu-id="daa9c-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="daa9c-110">Al asignar nombres a los cmdlets, no use ninguno de los siguientes caracteres: #, () {} [] &-/\ $; : "' < > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="daa9c-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="daa9c-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="daa9c-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="daa9c-112">Elección de un Sustantivo</span><span class="sxs-lookup"><span data-stu-id="daa9c-112">Choosing a Noun</span></span>

<span data-ttu-id="daa9c-113">Debe elegir un nombre específico.</span><span class="sxs-lookup"><span data-stu-id="daa9c-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="daa9c-114">Es mejor usar un Sustantivo Singular precedido de una versión abreviada del nombre del producto.</span><span class="sxs-lookup"><span data-stu-id="daa9c-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="daa9c-115">Un nombre de cmdlet de ejemplo de este tipo es "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="daa9c-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="daa9c-116">Elección de un verbo</span><span class="sxs-lookup"><span data-stu-id="daa9c-116">Choosing a Verb</span></span>

<span data-ttu-id="daa9c-117">Debe usar un verbo del conjunto de nombres de verbo de cmdlet aprobados.</span><span class="sxs-lookup"><span data-stu-id="daa9c-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="daa9c-118">Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="daa9c-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="daa9c-119">Definir la clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="daa9c-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="daa9c-120">Una vez que haya elegido un nombre de cmdlet, defina una clase .NET para implementar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="daa9c-121">Esta es la definición de clase de este cmdlet Get-proc de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="daa9c-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="daa9c-122">Observe que antes de la definición de clase, el atributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , con la sintaxis `[Cmdlet(verb, noun, ...)]`, se usa para identificar esta clase como un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="daa9c-123">Este es el único atributo necesario para todos los cmdlets y permite que el tiempo de ejecución de Windows PowerShell los llame correctamente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="daa9c-124">Puede establecer palabras clave de atributo para declarar más la clase si es necesario.</span><span class="sxs-lookup"><span data-stu-id="daa9c-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="daa9c-125">Tenga en cuenta que la declaración de atributo para la clase GetProcCommand de ejemplo declara solo los nombres de nombre y verbo para el cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="daa9c-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="daa9c-126">Para todas las clases de atributos de Windows PowerShell, las palabras clave que se pueden establecer corresponden a las propiedades de la clase de atributo.</span><span class="sxs-lookup"><span data-stu-id="daa9c-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="daa9c-127">Al asignar un nombre a la clase del cmdlet, se recomienda reflejar el nombre del cmdlet en el nombre de clase.</span><span class="sxs-lookup"><span data-stu-id="daa9c-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="daa9c-128">Para ello, use el formato "VerbNounCommand" y reemplace "Verb" y "Sustantivo" por el verbo y el sustantivo usados en el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="daa9c-129">Como se muestra en la definición de clase anterior, el cmdlet Get-proc de ejemplo define una clase denominada GetProcCommand, que deriva de la clase base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="daa9c-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="daa9c-130">Si desea definir un cmdlet que tenga acceso directamente al tiempo de ejecución de Windows PowerShell, la clase .NET debe derivarse de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="daa9c-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="daa9c-131">Para obtener más información sobre esta clase, consulte [crear un cmdlet que defina conjuntos de parámetros](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="daa9c-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="daa9c-132">La clase de un cmdlet debe marcarse explícitamente como Public.</span><span class="sxs-lookup"><span data-stu-id="daa9c-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="daa9c-133">Las clases que no están marcadas como públicas tendrán como valor predeterminado Internal y el tiempo de ejecución de Windows PowerShell no las encontrará.</span><span class="sxs-lookup"><span data-stu-id="daa9c-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="daa9c-134">Windows PowerShell usa el espacio de nombres [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) para sus clases de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="daa9c-135">Se recomienda colocar las clases de cmdlet en un espacio de nombres de comandos del espacio de nombres de la API, por ejemplo, xxx. PS. Commands.</span><span class="sxs-lookup"><span data-stu-id="daa9c-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="daa9c-136">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="daa9c-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="daa9c-137">La clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) proporciona tres métodos de procesamiento de entrada principales, al menos uno de los cuales el cmdlet debe reemplazar.</span><span class="sxs-lookup"><span data-stu-id="daa9c-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="daa9c-138">Para obtener más información sobre cómo Windows PowerShell procesa los registros, vea [Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="daa9c-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="daa9c-139">En el caso de todos los tipos de entrada, el tiempo de ejecución de Windows PowerShell llama a [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para habilitar el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="daa9c-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="daa9c-140">Si el cmdlet debe realizar algún proceso de preprocesamiento o configuración, puede hacerlo invalidando este método.</span><span class="sxs-lookup"><span data-stu-id="daa9c-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="daa9c-141">Windows PowerShell usa el término "registro" para describir el conjunto de valores de parámetro proporcionados cuando se llama a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="daa9c-142">Si el cmdlet acepta la entrada de canalización, debe invalidar el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y, opcionalmente, el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="daa9c-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="daa9c-143">Por ejemplo, un cmdlet podría invalidar ambos métodos si recopila toda la entrada mediante [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y, a continuación, opera en la entrada como un conjunto en lugar de un elemento a la vez, como hace el cmdlet `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="daa9c-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="daa9c-144">Si el cmdlet no toma la entrada de canalización, debe invalidar el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="daa9c-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="daa9c-145">Tenga en cuenta que este método se usa con frecuencia en lugar de [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cuando el cmdlet no puede operar en un elemento cada vez, como es el caso de un cmdlet de ordenación.</span><span class="sxs-lookup"><span data-stu-id="daa9c-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="daa9c-146">Dado que este cmdlet Get-proc de ejemplo debe recibir la entrada de canalización, invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) y usa las implementaciones predeterminadas para [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="daa9c-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="daa9c-147">La invalidación [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) recupera los procesos y los escribe en la línea de comandos mediante el método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="daa9c-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="daa9c-148">Aspectos que se deben recordar sobre el procesamiento de entradas</span><span class="sxs-lookup"><span data-stu-id="daa9c-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="daa9c-149">El origen predeterminado de la entrada es un objeto explícito (por ejemplo, una cadena) proporcionado por el usuario en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="daa9c-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="daa9c-150">Para obtener más información, vea [crear un cmdlet para procesar la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="daa9c-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="daa9c-151">Un método de procesamiento de entrada también puede recibir la entrada del objeto de salida de un cmdlet de nivel superior en la canalización.</span><span class="sxs-lookup"><span data-stu-id="daa9c-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="daa9c-152">Para obtener más información, vea [crear un cmdlet para procesar la entrada de canalización](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="daa9c-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="daa9c-153">Tenga en cuenta que el cmdlet puede recibir la entrada de una combinación de orígenes de línea de comandos y de canalización.</span><span class="sxs-lookup"><span data-stu-id="daa9c-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="daa9c-154">Es posible que el cmdlet de nivel inferior no devuelva mucho tiempo o que no se encuentre en absoluto.</span><span class="sxs-lookup"><span data-stu-id="daa9c-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="daa9c-155">Por ese motivo, el método de procesamiento de entrada del cmdlet no debe mantener bloqueos durante las llamadas a [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente los bloqueos para los que el ámbito se extiende más allá de la instancia del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="daa9c-156">Los cmdlets nunca deben llamar a [System. Console. WriteLine \*](/dotnet/api/System.Console.WriteLine) ni a su equivalente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="daa9c-157">Es posible que el cmdlet tenga variables de objeto para realizar la limpieza cuando termine el procesamiento (por ejemplo, si abre un identificador de archivo en el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y mantiene el identificador abierto para su uso por [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="daa9c-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="daa9c-158">Es importante recordar que el tiempo de ejecución de Windows PowerShell no siempre llama al método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , que debe realizar la limpieza de objetos.</span><span class="sxs-lookup"><span data-stu-id="daa9c-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="daa9c-159">Por ejemplo, no se puede llamar a [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) si el cmdlet se cancela a la mitad o si se produce un error de terminación en cualquier parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="daa9c-160">Por lo tanto, un cmdlet que requiera la limpieza de objetos debe implementar el patrón [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluido el finalizador, de modo que el tiempo de ejecución pueda llamar a [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y [System. IDisposable. Dispose \*](/dotnet/api/System.IDisposable.Dispose) al final del procesamiento.</span><span class="sxs-lookup"><span data-stu-id="daa9c-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="daa9c-161">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="daa9c-161">Code Sample</span></span>

<span data-ttu-id="daa9c-162">Para obtener el C# código de ejemplo completo, vea el [ejemplo de GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="daa9c-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="daa9c-163">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="daa9c-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="daa9c-164">Windows PowerShell pasa información entre cmdlets mediante objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="daa9c-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="daa9c-165">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="daa9c-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="daa9c-166">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="daa9c-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="daa9c-167">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="daa9c-167">Building the Cmdlet</span></span>

<span data-ttu-id="daa9c-168">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daa9c-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="daa9c-169">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="daa9c-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="daa9c-170">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="daa9c-170">Testing the Cmdlet</span></span>

<span data-ttu-id="daa9c-171">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="daa9c-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="daa9c-172">El código de nuestro cmdlet Get-proc de ejemplo es pequeño, pero todavía usa el tiempo de ejecución de Windows PowerShell y un objeto .NET existente, que es suficiente para que resulte útil.</span><span class="sxs-lookup"><span data-stu-id="daa9c-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="daa9c-173">Vamos a probarlo para comprender mejor lo que puede hacer Get-proc y cómo puede usarse su salida.</span><span class="sxs-lookup"><span data-stu-id="daa9c-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="daa9c-174">Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="daa9c-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="daa9c-175">Inicie Windows PowerShell y obtenga los procesos actuales que se ejecutan en el equipo.</span><span class="sxs-lookup"><span data-stu-id="daa9c-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="daa9c-176">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="daa9c-177">Asigne una variable a los resultados del cmdlet para facilitar la manipulación.</span><span class="sxs-lookup"><span data-stu-id="daa9c-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="daa9c-178">Obtiene el número de procesos.</span><span class="sxs-lookup"><span data-stu-id="daa9c-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="daa9c-179">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="daa9c-180">Recuperar un proceso específico.</span><span class="sxs-lookup"><span data-stu-id="daa9c-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="daa9c-181">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="daa9c-182">Obtiene la hora de inicio de este proceso.</span><span class="sxs-lookup"><span data-stu-id="daa9c-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="daa9c-183">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="daa9c-184">Obtiene los procesos para los que el número de identificadores es mayor que 500 y ordena el resultado.</span><span class="sxs-lookup"><span data-stu-id="daa9c-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="daa9c-185">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="daa9c-186">Use el cmdlet `Get-Member` para mostrar las propiedades disponibles para cada proceso.</span><span class="sxs-lookup"><span data-stu-id="daa9c-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="daa9c-187">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa9c-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="daa9c-188">Véase también</span><span class="sxs-lookup"><span data-stu-id="daa9c-188">See Also</span></span>

[<span data-ttu-id="daa9c-189">Crear un cmdlet para procesar la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="daa9c-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="daa9c-190">Crear un cmdlet para procesar la entrada de canalización</span><span class="sxs-lookup"><span data-stu-id="daa9c-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="daa9c-191">Cómo crear un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="daa9c-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="daa9c-192">[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="daa9c-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="daa9c-193">[Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="daa9c-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="daa9c-194">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="daa9c-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="daa9c-195">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="daa9c-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="daa9c-196">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="daa9c-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
