---
title: Agregar alias, expansión de caracteres comodín y ayuda para los parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415660"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="f12c6-102">Adición de alias, expansión de caracteres comodín y Ayuda a los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f12c6-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="f12c6-103">En esta sección se describe cómo agregar alias, expansión de caracteres comodín y mensajes de ayuda a los parámetros del cmdlet Stop-proc (que se describe en [creación de un cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="f12c6-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="f12c6-104">Este cmdlet Stop-proc intenta detener los procesos que se recuperan con el cmdlet Get-proc (descrito en [creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="f12c6-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="f12c6-105">Definición del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f12c6-105">Defining the Cmdlet</span></span>

<span data-ttu-id="f12c6-106">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f12c6-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="f12c6-107">Dado que está escribiendo un cmdlet para cambiar el sistema, debe denominarse en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="f12c6-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="f12c6-108">Dado que este cmdlet detiene los procesos del sistema, utiliza el verbo "STOP", definido por la clase [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con el nombre "proc" para indicar el proceso.</span><span class="sxs-lookup"><span data-stu-id="f12c6-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="f12c6-109">Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f12c6-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="f12c6-110">El código siguiente es la definición de clase para este cmdlet Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="f12c6-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="f12c6-111">Definir parámetros para la modificación del sistema</span><span class="sxs-lookup"><span data-stu-id="f12c6-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="f12c6-112">El cmdlet debe definir parámetros que admitan las modificaciones del sistema y los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="f12c6-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="f12c6-113">El cmdlet debe definir un parámetro `Name` o un equivalente para que el cmdlet pueda modificar el sistema mediante algún tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="f12c6-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="f12c6-114">Además, el cmdlet debe definir los parámetros `Force` y `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="f12c6-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="f12c6-115">Para obtener más información acerca de estos parámetros, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="f12c6-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="f12c6-116">Definir un alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="f12c6-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="f12c6-117">Un alias de parámetro puede ser un nombre alternativo o un nombre corto de 1 letra o 2 Letras bien definido para un parámetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f12c6-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="f12c6-118">En ambos casos, el objetivo de usar alias es simplificar la entrada del usuario desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f12c6-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="f12c6-119">Windows PowerShell admite alias de parámetro mediante el atributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , que usa la sintaxis de declaración [alias ()].</span><span class="sxs-lookup"><span data-stu-id="f12c6-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="f12c6-120">En el código siguiente se muestra cómo se agrega un alias al parámetro `Name`.</span><span class="sxs-lookup"><span data-stu-id="f12c6-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="f12c6-121">Además de usar el atributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , el tiempo de ejecución de Windows PowerShell realiza una coincidencia parcial de nombres, aunque no se especifique ningún alias.</span><span class="sxs-lookup"><span data-stu-id="f12c6-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="f12c6-122">Por ejemplo, si el cmdlet tiene un parámetro `FileName` y éste es el único parámetro que comienza con `F`, el usuario podría escribir `Filename`, `Filenam`, `File`, `Fi`o `F` y seguir reconociendo la entrada como el parámetro `FileName`.</span><span class="sxs-lookup"><span data-stu-id="f12c6-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="f12c6-123">Crear ayuda para parámetros</span><span class="sxs-lookup"><span data-stu-id="f12c6-123">Creating Help for Parameters</span></span>

<span data-ttu-id="f12c6-124">Windows PowerShell le permite crear ayuda para los parámetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f12c6-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="f12c6-125">Haga esto para cualquier parámetro utilizado para la modificación del sistema y los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="f12c6-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="f12c6-126">Para que cada parámetro admita la ayuda, puede establecer la palabra clave de atributo `HelpMessage` en la declaración de atributo [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f12c6-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="f12c6-127">Esta palabra clave define el texto que se va a mostrar al usuario para obtener ayuda sobre el uso del parámetro.</span><span class="sxs-lookup"><span data-stu-id="f12c6-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="f12c6-128">También puede establecer la palabra clave `HelpMessageBaseName` para identificar el nombre base de un recurso que se va a usar para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="f12c6-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="f12c6-129">Si establece esta palabra clave, también debe establecer la palabra clave `HelpMessageResourceId` para especificar el identificador de recursos.</span><span class="sxs-lookup"><span data-stu-id="f12c6-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="f12c6-130">El siguiente código de este cmdlet Stop-proc define la palabra clave del atributo `HelpMessage` para el parámetro `Name`.</span><span class="sxs-lookup"><span data-stu-id="f12c6-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f12c6-131">Reemplazar un método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="f12c6-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f12c6-132">El cmdlet debe invalidar un método de procesamiento de entrada, lo que suele ser [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="f12c6-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="f12c6-133">Al modificar el sistema, el cmdlet debe llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) para permitir que el usuario proporcione comentarios antes de que se realice un cambio.</span><span class="sxs-lookup"><span data-stu-id="f12c6-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="f12c6-134">Para obtener más información acerca de estos métodos, consulte [crear un cmdlet que modifique el sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="f12c6-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="f12c6-135">Compatibilidad con la expansión de caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="f12c6-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="f12c6-136">Para permitir la selección de varios objetos, el cmdlet puede usar las clases [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) y [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) para proporcionar compatibilidad con la expansión de caracteres comodín para la entrada de parámetros.</span><span class="sxs-lookup"><span data-stu-id="f12c6-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="f12c6-137">Algunos ejemplos de patrones de caracteres comodín son LSA \*, \*. txt y [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="f12c6-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="f12c6-138">Use el carácter de comilla inversa (') como carácter de escape cuando el patrón contenga un carácter que se deba usar literalmente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="f12c6-139">Las expansiones de comodín de los nombres de archivo y de ruta de acceso son ejemplos de escenarios comunes en los que el cmdlet puede querer permitir la compatibilidad con entradas de ruta de acceso cuando se requiere la selección de varios objetos.</span><span class="sxs-lookup"><span data-stu-id="f12c6-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="f12c6-140">Un caso común está en el sistema de archivos, en el que un usuario desea ver todos los archivos que residen en la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="f12c6-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="f12c6-141">Solo necesitará una implementación personalizada de coincidencia de patrones de caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="f12c6-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="f12c6-142">En este caso, el cmdlet debe ser compatible con la especificación de POSIX 1003,2, 3,13 completa para la expansión de caracteres comodín o el siguiente subconjunto simplificado:</span><span class="sxs-lookup"><span data-stu-id="f12c6-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="f12c6-143">**Signo de interrogación (?).**</span><span class="sxs-lookup"><span data-stu-id="f12c6-143">**Question mark (?).**</span></span> <span data-ttu-id="f12c6-144">Coincide con cualquier carácter que se encuentra en la ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="f12c6-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="f12c6-145">**Asterisco (\*).**</span><span class="sxs-lookup"><span data-stu-id="f12c6-145">**Asterisk (\*).**</span></span> <span data-ttu-id="f12c6-146">Coincide con cero o más caracteres que comienzan en la ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="f12c6-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="f12c6-147">**Corchete de apertura ([).**</span><span class="sxs-lookup"><span data-stu-id="f12c6-147">**Open bracket ([).**</span></span> <span data-ttu-id="f12c6-148">Introduce una expresión entre corchetes de patrón que puede contener caracteres o un intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f12c6-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="f12c6-149">Si se requiere un intervalo, se usa un guión (-) para indicar el intervalo.</span><span class="sxs-lookup"><span data-stu-id="f12c6-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="f12c6-150">**Corchete de cierre (]).**</span><span class="sxs-lookup"><span data-stu-id="f12c6-150">**Close bracket (]).**</span></span> <span data-ttu-id="f12c6-151">Finaliza una expresión de corchete de patrón.</span><span class="sxs-lookup"><span data-stu-id="f12c6-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="f12c6-152">**Carácter de escape de comilla inversa (').**</span><span class="sxs-lookup"><span data-stu-id="f12c6-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="f12c6-153">Indica que el siguiente carácter debe tomarse literalmente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="f12c6-154">Tenga en cuenta que al especificar el carácter de comilla inversa desde la línea de comandos (en lugar de especificarlo mediante programación), el carácter de escape de comilla inversa debe especificarse dos veces.</span><span class="sxs-lookup"><span data-stu-id="f12c6-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="f12c6-155">Para obtener más información sobre los patrones de caracteres comodín, consulte [compatibilidad con caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f12c6-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="f12c6-156">El código siguiente muestra cómo establecer opciones de carácter comodín y definir el patrón de caracteres comodín que se usa para resolver el parámetro `Name` para este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f12c6-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="f12c6-157">En el código siguiente se muestra cómo comprobar si el nombre del proceso coincide con el patrón de caracteres comodín definido.</span><span class="sxs-lookup"><span data-stu-id="f12c6-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="f12c6-158">Tenga en cuenta que, en este caso, si el nombre del proceso no coincide con el patrón, el cmdlet continúa para obtener el nombre del proceso siguiente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="f12c6-159">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="f12c6-159">Code Sample</span></span>

<span data-ttu-id="f12c6-160">Para obtener el C# código de ejemplo completo, vea el [ejemplo de StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f12c6-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="f12c6-161">Definir tipos de objeto y formato</span><span class="sxs-lookup"><span data-stu-id="f12c6-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="f12c6-162">Windows PowerShell pasa información entre cmdlets mediante objetos .net.</span><span class="sxs-lookup"><span data-stu-id="f12c6-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="f12c6-163">Por lo tanto, es posible que un cmdlet tenga que definir su propio tipo o que el cmdlet tenga que extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f12c6-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f12c6-164">Para obtener más información sobre la definición de nuevos tipos o la extensión de tipos existentes, vea [extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f12c6-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f12c6-165">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f12c6-165">Building the Cmdlet</span></span>

<span data-ttu-id="f12c6-166">Después de implementar un cmdlet, debe registrarse con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f12c6-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f12c6-167">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f12c6-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f12c6-168">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f12c6-168">Testing the Cmdlet</span></span>

<span data-ttu-id="f12c6-169">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f12c6-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="f12c6-170">Vamos a probar el cmdlet Stop-proc de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f12c6-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="f12c6-171">Para obtener más información sobre el uso de cmdlets desde la línea de comandos, consulte la [Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f12c6-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="f12c6-172">Inicie Windows PowerShell y use STOP-proc para detener un proceso con el alias processName para el parámetro `Name`.</span><span class="sxs-lookup"><span data-stu-id="f12c6-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="f12c6-173">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="f12c6-174">Realice la siguiente entrada en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f12c6-174">Make the following entry on the command line.</span></span> <span data-ttu-id="f12c6-175">Dado que el parámetro name es obligatorio, se le pedirá que lo indique.</span><span class="sxs-lookup"><span data-stu-id="f12c6-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="f12c6-176">Escribiendo "!?"</span><span class="sxs-lookup"><span data-stu-id="f12c6-176">Entering "!?"</span></span> <span data-ttu-id="f12c6-177">muestra el texto de ayuda asociado al parámetro.</span><span class="sxs-lookup"><span data-stu-id="f12c6-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="f12c6-178">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="f12c6-179">Ahora realice la siguiente entrada para detener todos los procesos que coinciden con el patrón de carácter comodín "\* note\*".</span><span class="sxs-lookup"><span data-stu-id="f12c6-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="f12c6-180">Se le pedirá antes de detener cada proceso que coincida con el patrón.</span><span class="sxs-lookup"><span data-stu-id="f12c6-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="f12c6-181">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="f12c6-182">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="f12c6-183">Aparece la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="f12c6-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="f12c6-184">Véase también</span><span class="sxs-lookup"><span data-stu-id="f12c6-184">See Also</span></span>

[<span data-ttu-id="f12c6-185">Crear un cmdlet que modifique el sistema</span><span class="sxs-lookup"><span data-stu-id="f12c6-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="f12c6-186">Cómo crear un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f12c6-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="f12c6-187">[Extender tipos de objeto y formato](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f12c6-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="f12c6-188">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f12c6-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="f12c6-189">Compatibilidad con caracteres comodín en parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f12c6-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="f12c6-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f12c6-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
