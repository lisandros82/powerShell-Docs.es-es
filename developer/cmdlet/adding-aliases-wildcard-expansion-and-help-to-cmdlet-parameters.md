---
title: Agregar alias, expansión de caracteres comodín y ayudar a los parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859331"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="2b264-102">Adición de alias, expansión de caracteres comodín y Ayuda a los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="2b264-103">En esta sección se describe cómo agregar los alias, expansión de caracteres comodín, y los mensajes de ayuda a los parámetros del cmdlet Stop-Proc (se describe en [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="2b264-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="2b264-104">Este cmdlet Stop-Proc intenta detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="2b264-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="2b264-105">Temas de esta sección incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2b264-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="2b264-106">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="2b264-107">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="2b264-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="2b264-108">Definir un Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="2b264-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="2b264-109">Ayuda para los parámetros de creación</span><span class="sxs-lookup"><span data-stu-id="2b264-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="2b264-110">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="2b264-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="2b264-111">Compatibilidad con la expansión de caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="2b264-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="2b264-112">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="2b264-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="2b264-113">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="2b264-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="2b264-114">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="2b264-115">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="2b264-116">Definir el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-116">Defining the Cmdlet</span></span>

<span data-ttu-id="2b264-117">El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b264-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="2b264-118">Dado que está escribiendo un cmdlet para cambiar el sistema, debe llamarse en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="2b264-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="2b264-119">Dado que este cmdlet detiene los procesos del sistema, utiliza el verbo "Stop", definido por el [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (clase), con el sustantivo "Proc" para indicar el proceso.</span><span class="sxs-lookup"><span data-stu-id="2b264-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="2b264-120">Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="2b264-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="2b264-121">El código siguiente es la definición de clase para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="2b264-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="2b264-122">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="2b264-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="2b264-123">El cmdlet debe definir los parámetros que las modificaciones del sistema de soporte técnico y comentarios del usuario.</span><span class="sxs-lookup"><span data-stu-id="2b264-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="2b264-124">El cmdlet debe definir un `Name` parámetro o un equivalente para que el cmdlet pueda modificar el sistema por algún tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="2b264-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="2b264-125">Además, debe definir el cmdlet la `Force` y `PassThru` parámetros.</span><span class="sxs-lookup"><span data-stu-id="2b264-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="2b264-126">Para obtener más información acerca de estos parámetros, vea [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="2b264-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="2b264-127">Definir un Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="2b264-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="2b264-128">Un alias de parámetro puede ser un nombre alternativo o un bien definido letra de 1 o 2 nombre corto para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b264-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="2b264-129">En ambos casos, el objetivo de uso de alias es simplificar la entrada de usuario desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="2b264-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="2b264-130">Windows PowerShell es compatible con alias de parámetro a través de la [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, que utiliza la sintaxis de declaración [Alias()].</span><span class="sxs-lookup"><span data-stu-id="2b264-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="2b264-131">El código siguiente muestra cómo se agrega un alias para el `Name` parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b264-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="2b264-132">Además de utilizar el [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, el tiempo de ejecución de Windows PowerShell realiza la coincidencia de nombres parciales, incluso si no se especifican ningún alias.</span><span class="sxs-lookup"><span data-stu-id="2b264-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="2b264-133">Por ejemplo, si su cmdlet tiene un `FileName` parámetro y que es el único parámetro que empieza por `F`, el usuario puede escribir `Filename`, `Filenam`, `File`, `Fi`, o `F` y aún reconoce los entrada de la `FileName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b264-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="2b264-134">Ayuda para los parámetros de creación</span><span class="sxs-lookup"><span data-stu-id="2b264-134">Creating Help for Parameters</span></span>

<span data-ttu-id="2b264-135">Windows PowerShell le permite crear ayuda para los parámetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b264-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="2b264-136">Hacer esto para cualquier parámetro que se usa para los comentarios de usuario y la modificación del sistema.</span><span class="sxs-lookup"><span data-stu-id="2b264-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="2b264-137">Para que cada parámetro admitir la Ayuda, puede establecer el `HelpMessage` atributo palabra clave en el [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaración de atributos.</span><span class="sxs-lookup"><span data-stu-id="2b264-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="2b264-138">Esta palabra clave define el texto para mostrar al usuario para asistencia en el uso del parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b264-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="2b264-139">También puede establecer el `HelpMessageBaseName` palabra clave para identificar el nombre de base de un recurso que se usará para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="2b264-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="2b264-140">Si establece esta palabra clave, también debe establecer el `HelpMessageResourceId` palabra clave para especificar el identificador de recurso.</span><span class="sxs-lookup"><span data-stu-id="2b264-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="2b264-141">El siguiente código de este cmdlet Stop-Proc define la `HelpMessage` atributo palabra clave para el `Name` parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b264-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="2b264-142">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="2b264-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="2b264-143">El cmdlet debe invalidar una método de procesamiento de entrada, con más frecuencia esto será [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="2b264-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="2b264-144">Cuando se modifica el sistema, el cmdlet debe llamar a la [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para permitir que el usuario para proporcionar comentarios antes de que se realiza un cambio.</span><span class="sxs-lookup"><span data-stu-id="2b264-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="2b264-145">Para obtener más información acerca de estos métodos, consulte [creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="2b264-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="2b264-146">Compatibilidad con la expansión de caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="2b264-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="2b264-147">Para permitir la selección de varios objetos, puede usar el cmdlet la [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) y [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) las clases para proporcionar compatibilidad con la expansión de caracteres comodín para el parámetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="2b264-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="2b264-148">Ejemplos de patrones de caracteres comodín son lsa \* \*.txt y [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="2b264-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="2b264-149">Use el carácter de comilla invertida (') como carácter de escape cuando el modelo contiene un carácter que se debe usar literalmente.</span><span class="sxs-lookup"><span data-stu-id="2b264-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="2b264-150">Las expansiones de comodín de nombres de archivo y ruta de acceso son ejemplos de escenarios comunes en el cmdlet puede que desee permitir la compatibilidad para las entradas de ruta de acceso cuando se requiere la selección de varios objetos.</span><span class="sxs-lookup"><span data-stu-id="2b264-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="2b264-151">Un caso común es en el sistema de archivos, donde un usuario desea ver todos los archivos que residen en la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="2b264-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="2b264-152">Es necesario una implementación de coincidencia de patrón comodín personalizados solo en raras ocasiones.</span><span class="sxs-lookup"><span data-stu-id="2b264-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="2b264-153">En este caso, el cmdlet debe admitir la versión 1003.2 POSIX completa, 3,13 especificación para la expansión de caracteres comodín o el siguiente subconjunto simplificado:</span><span class="sxs-lookup"><span data-stu-id="2b264-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="2b264-154">**Signo de interrogación (?).**</span><span class="sxs-lookup"><span data-stu-id="2b264-154">**Question mark (?).**</span></span> <span data-ttu-id="2b264-155">Coincide con cualquier carácter que ocupa la posición especificada.</span><span class="sxs-lookup"><span data-stu-id="2b264-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="2b264-156">**Asterisk (\*).**</span><span class="sxs-lookup"><span data-stu-id="2b264-156">**Asterisk (\*).**</span></span> <span data-ttu-id="2b264-157">Coincide con cero o más caracteres, empezando en la ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="2b264-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="2b264-158">**Corchete de apertura ([]).**</span><span class="sxs-lookup"><span data-stu-id="2b264-158">**Open bracket ([).**</span></span> <span data-ttu-id="2b264-159">Presenta una expresión entre corchetes de patrón que puede contener caracteres o un intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2b264-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="2b264-160">Si se requiere un intervalo, un guión (-) se utiliza para indicar el intervalo.</span><span class="sxs-lookup"><span data-stu-id="2b264-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="2b264-161">**Corchete de cierre (]).**</span><span class="sxs-lookup"><span data-stu-id="2b264-161">**Close bracket (]).**</span></span> <span data-ttu-id="2b264-162">Finaliza una expresión entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="2b264-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="2b264-163">**Carácter de escape (') comilla.**</span><span class="sxs-lookup"><span data-stu-id="2b264-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="2b264-164">Indica que se debe tomar literalmente el carácter siguiente.</span><span class="sxs-lookup"><span data-stu-id="2b264-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="2b264-165">Tenga en cuenta que al especificar el carácter de comilla desde la línea de comandos (en lugar de especificar mediante programación), el carácter de comilla escape debe especificarse dos veces.</span><span class="sxs-lookup"><span data-stu-id="2b264-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="2b264-166">Para obtener más información sobre los patrones de caracteres comodín, consulte [que admiten caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2b264-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="2b264-167">El código siguiente muestra cómo establecer las opciones de comodín y definir el modelo de carácter comodín se utiliza para resolver el `Name` parámetro para este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b264-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="2b264-168">El código siguiente se muestra cómo probar si el nombre del proceso coincide con el patrón comodín definido.</span><span class="sxs-lookup"><span data-stu-id="2b264-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="2b264-169">Tenga en cuenta que, en este caso, si el nombre del proceso no coincide con el patrón, el cmdlet continúa en obtener el nombre del proceso siguiente.</span><span class="sxs-lookup"><span data-stu-id="2b264-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="2b264-170">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="2b264-170">Code Sample</span></span>

<span data-ttu-id="2b264-171">Para la completa C# código de ejemplo, vea [StopProcessSample03 ejemplo](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2b264-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="2b264-172">Definir tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="2b264-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="2b264-173">Windows PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="2b264-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="2b264-174">Por lo tanto, un cmdlet que deba definir su propio tipo o el cmdlet puede necesitar extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b264-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="2b264-175">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="2b264-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="2b264-176">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-176">Building the Cmdlet</span></span>

<span data-ttu-id="2b264-177">Después de implementar un cmdlet, se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b264-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="2b264-178">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="2b264-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="2b264-179">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-179">Testing the Cmdlet</span></span>

<span data-ttu-id="2b264-180">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="2b264-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="2b264-181">Vamos a probar el cmdlet Stop-Proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="2b264-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="2b264-182">Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2b264-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="2b264-183">Inicie Windows PowerShell y use Stop-Proc para detener un proceso mediante el alias de nombre de proceso para el `Name` parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b264-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="2b264-184">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="2b264-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="2b264-185">Escriba lo siguiente en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="2b264-185">Make the following entry on the command line.</span></span> <span data-ttu-id="2b264-186">Dado que el parámetro de nombre es obligatorio, le para él.</span><span class="sxs-lookup"><span data-stu-id="2b264-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="2b264-187">Escribir "!?"</span><span class="sxs-lookup"><span data-stu-id="2b264-187">Entering "!?"</span></span> <span data-ttu-id="2b264-188">aparece el texto de ayuda asociado al parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b264-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="2b264-189">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="2b264-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="2b264-190">Ahora escriba lo siguiente para detener todos los procesos que coinciden con el patrón de carácter comodín "\* Nota\*".</span><span class="sxs-lookup"><span data-stu-id="2b264-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="2b264-191">Se le solicite antes de detener todos los procesos que coincide con el modelo.</span><span class="sxs-lookup"><span data-stu-id="2b264-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="2b264-192">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="2b264-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="2b264-193">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="2b264-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="2b264-194">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="2b264-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="2b264-195">Véase también</span><span class="sxs-lookup"><span data-stu-id="2b264-195">See Also</span></span>

[<span data-ttu-id="2b264-196">Crear un Cmdlet que modifique el sistema</span><span class="sxs-lookup"><span data-stu-id="2b264-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="2b264-197">Creación de un Cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b264-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="2b264-198">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="2b264-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="2b264-199">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="2b264-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2b264-200">Compatibilidad con caracteres comodín en los parámetros de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b264-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="2b264-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2b264-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
