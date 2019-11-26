---
title: Creación de un cmdlet para obtener acceso a un almacén de datos
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 3096965ba9f99f70994f2fb5b180cc58691b04f8
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415698"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="0fb7a-102">Creación de un cmdlet para obtener acceso a un almacén de datos</span><span class="sxs-lookup"><span data-stu-id="0fb7a-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="0fb7a-103">En esta sección se describe cómo crear un cmdlet que acceda a los datos almacenados mediante un proveedor de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="0fb7a-104">Este tipo de cmdlet usa la infraestructura del proveedor de Windows PowerShell del tiempo de ejecución de Windows PowerShell y, por lo tanto, la clase de cmdlet debe derivar de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="0fb7a-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="0fb7a-105">El cmdlet Select-Str que se describe aquí puede buscar y seleccionar cadenas en un archivo u objeto.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="0fb7a-106">Los patrones que se usan para identificar la cadena se pueden especificar explícitamente a través del parámetro `Path` del cmdlet o implícitamente a través del parámetro `Script`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="0fb7a-107">El cmdlet está diseñado para usar cualquier proveedor de Windows PowerShell que derive de [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="0fb7a-108">Por ejemplo, el cmdlet puede especificar el proveedor del sistema de archivos o el proveedor de variables proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="0fb7a-109">Para más información aboutWindows los proveedores de PowerShell, consulte [diseño del proveedor de Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="0fb7a-110">Definir la clase de cmdlet</span><span class="sxs-lookup"><span data-stu-id="0fb7a-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="0fb7a-111">El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="0fb7a-112">Este cmdlet detecta ciertas cadenas, por lo que el nombre del verbo elegido aquí es "Select", definido por la clase [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) .</span><span class="sxs-lookup"><span data-stu-id="0fb7a-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="0fb7a-113">El nombre de sustantivo "STR" se usa porque el cmdlet actúa en las cadenas.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="0fb7a-114">En la declaración siguiente, tenga en cuenta que el verbo de cmdlet y el nombre de sustantivo se reflejan en el nombre de la clase de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="0fb7a-115">Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="0fb7a-116">La clase .NET de este cmdlet debe derivarse de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , ya que proporciona la compatibilidad necesaria para que el motor en tiempo de ejecución de Windows PowerShell exponga la infraestructura del proveedor de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="0fb7a-117">Tenga en cuenta que este cmdlet también hace uso de las clases de expresiones regulares .NET Framework, como [System. Text. RegularExpressions. Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="0fb7a-118">El código siguiente es la definición de clase de este cmdlet Select-Str.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="0fb7a-119">Este cmdlet define un conjunto de parámetros predeterminado agregando la palabra clave del atributo `DefaultParameterSetName` a la declaración de clase.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="0fb7a-120">Se utiliza el conjunto de parámetros predeterminado `PatternParameterSet` cuando no se especifica el parámetro `Script`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="0fb7a-121">Para obtener más información acerca de este conjunto de parámetros, vea la descripción de los parámetros `Pattern` y `Script` en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="0fb7a-122">Definir parámetros para el acceso a datos</span><span class="sxs-lookup"><span data-stu-id="0fb7a-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="0fb7a-123">Este cmdlet define varios parámetros que permiten al usuario obtener acceso a los datos almacenados y examinarlos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="0fb7a-124">Estos parámetros incluyen un parámetro `Path` que indica la ubicación del almacén de datos, un parámetro `Pattern` que especifica el patrón que se va a usar en la búsqueda y otros parámetros que admiten la forma en que se realiza la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="0fb7a-125">Para obtener más información sobre los conceptos básicos de la definición de parámetros, vea [agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="0fb7a-126">Declarar el parámetro Path</span><span class="sxs-lookup"><span data-stu-id="0fb7a-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="0fb7a-127">Para buscar el almacén de datos, este cmdlet debe usar una ruta de acceso de Windows PowerShell para identificar el proveedor de Windows PowerShell que está diseñado para acceder al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="0fb7a-128">Por lo tanto, define un parámetro `Path` de tipo matriz de cadenas para indicar la ubicación del proveedor.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="0fb7a-129">Tenga en cuenta que este parámetro pertenece a dos conjuntos de parámetros diferentes y que tiene un alias.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="0fb7a-130">Dos atributos [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaran que el parámetro `Path` pertenece al `ScriptParameterSet` y `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="0fb7a-131">Para obtener más información sobre los conjuntos de parámetros, vea [Agregar conjuntos de parámetros a un cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="0fb7a-132">El atributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) declara un alias `PSPath` para el parámetro `Path`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="0fb7a-133">Se recomienda encarecidamente declarar este alias para la coherencia con otros cmdlets que tienen acceso a los proveedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="0fb7a-134">Para más información aboutWindows las rutas de acceso de PowerShell, consulte "conceptos de la ruta de PowerShell" en [Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="0fb7a-135">Declarar el parámetro Pattern</span><span class="sxs-lookup"><span data-stu-id="0fb7a-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="0fb7a-136">Para especificar los patrones que se van a buscar, este cmdlet declara un parámetro `Pattern` que es una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="0fb7a-137">Se devuelve un resultado positivo cuando se encuentra cualquiera de los patrones en el almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="0fb7a-138">Tenga en cuenta que estos patrones se pueden compilar en una matriz de expresiones regulares compiladas o en una matriz de patrones comodín que se usan para las búsquedas literales.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="0fb7a-139">Cuando se especifica este parámetro, el cmdlet usa el conjunto de parámetros predeterminado `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="0fb7a-140">En este caso, el cmdlet usa los patrones especificados aquí para seleccionar cadenas.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="0fb7a-141">Por el contrario, el parámetro `Script` también podría usarse para proporcionar un script que contenga los patrones.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="0fb7a-142">Los parámetros `Script` y `Pattern` definen dos conjuntos de parámetros independientes, por lo que son mutuamente excluyentes.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="0fb7a-143">Declarar parámetros de compatibilidad de búsqueda</span><span class="sxs-lookup"><span data-stu-id="0fb7a-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="0fb7a-144">Este cmdlet define los siguientes parámetros de soporte técnico que se pueden usar para modificar las capacidades de búsqueda del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="0fb7a-145">El parámetro `Script` especifica un bloque de script que se puede usar para proporcionar un mecanismo de búsqueda alternativo para el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="0fb7a-146">El script debe contener los patrones que se usan para buscar coincidencias y devolver un objeto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .</span><span class="sxs-lookup"><span data-stu-id="0fb7a-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="0fb7a-147">Tenga en cuenta que este parámetro es también el parámetro único que identifica el conjunto de parámetros `ScriptParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="0fb7a-148">Cuando el tiempo de ejecución de Windows PowerShell ve este parámetro, solo usa los parámetros que pertenecen al conjunto de parámetros `ScriptParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="0fb7a-149">El parámetro `SimpleMatch` es un parámetro de modificador que indica si el cmdlet debe coincidir explícitamente con los patrones a medida que se proporcionan.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="0fb7a-150">Cuando el usuario especifica el parámetro en la línea de comandos (`true`), el cmdlet usa los patrones a medida que se proporcionan.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="0fb7a-151">Si no se especifica el parámetro (`false`), el cmdlet usa expresiones regulares.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="0fb7a-152">El valor predeterminado de este parámetro es `false`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="0fb7a-153">El parámetro `CaseSensitive` es un parámetro de modificador que indica si se realiza una búsqueda con distinción de mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="0fb7a-154">Cuando el usuario especifica el parámetro en la línea de comandos (`true`), el cmdlet comprueba si hay caracteres en mayúsculas y minúsculas al comparar patrones.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="0fb7a-155">Si no se especifica el parámetro (`false`), el cmdlet no distingue entre mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="0fb7a-156">Por ejemplo, "Perfile" y "Perfile" se devolverían como aciertos positivos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="0fb7a-157">El valor predeterminado de este parámetro es `false`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="0fb7a-158">Los parámetros `Exclude` y `Include` identifican los elementos que se excluyen explícitamente o se incluyen en la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="0fb7a-159">De forma predeterminada, el cmdlet buscará en todos los elementos del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="0fb7a-160">Sin embargo, para limitar la búsqueda realizada por el cmdlet, estos parámetros se pueden usar para indicar explícitamente que los elementos que se van a incluir en la búsqueda se han omitido.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="0fb7a-161">Declarar conjuntos de parámetros</span><span class="sxs-lookup"><span data-stu-id="0fb7a-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="0fb7a-162">Este cmdlet usa dos conjuntos de parámetros (`ScriptParameterSet` y `PatternParameterSet`, que es el valor predeterminado), como los nombres de dos conjuntos de parámetros que se usan en el acceso a datos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="0fb7a-163">`PatternParameterSet` es el conjunto de parámetros predeterminado y se usa cuando se especifica el parámetro `Pattern`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="0fb7a-164">`ScriptParameterSet` se utiliza cuando el usuario especifica un mecanismo de búsqueda alternativo a través del parámetro `Script`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="0fb7a-165">Para obtener más información sobre los conjuntos de parámetros, vea [Agregar conjuntos de parámetros a un cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="0fb7a-166">Reemplazar métodos de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="0fb7a-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="0fb7a-167">Los cmdlets deben invalidar uno o varios métodos de procesamiento de entrada para la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="0fb7a-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="0fb7a-168">Para obtener más información acerca de los métodos de procesamiento de entrada, consulte [crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="0fb7a-169">Este cmdlet invalida el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para compilar una matriz de expresiones regulares compiladas en el inicio.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="0fb7a-170">Esto aumenta el rendimiento durante las búsquedas que no utilizan la coincidencia simple.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="0fb7a-171">Este cmdlet también invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para procesar las selecciones de cadena que el usuario realiza en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="0fb7a-172">Escribe los resultados de la selección de cadena en forma de un objeto personalizado llamando a un método **MatchString** privado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="0fb7a-173">Acceder al contenido</span><span class="sxs-lookup"><span data-stu-id="0fb7a-173">Accessing Content</span></span>

<span data-ttu-id="0fb7a-174">El cmdlet debe abrir el proveedor indicado por la ruta de acceso de Windows PowerShell para que pueda acceder a los datos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="0fb7a-175">El objeto [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) del espacio de ejecución se usa para el acceso al proveedor, mientras que la propiedad [System. Management. Automation. PSCmdlet. Invokeprovider \*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) del cmdlet se usa para abrir el proveedor.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="0fb7a-176">El acceso al contenido se proporciona mediante la recuperación del objeto [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) para el proveedor abierto.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="0fb7a-177">Este cmdlet Select-Str de ejemplo usa la propiedad [System. Management. Automation. Providerintrinsics. Content \*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) para exponer el contenido que se va a examinar.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="0fb7a-178">Después, puede llamar al método [System. Management. Automation. Contentcmdletproviderintrinsics. getReader \*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) , pasando la ruta de acceso de Windows PowerShell necesaria.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0fb7a-179">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="0fb7a-179">Code Sample</span></span>

<span data-ttu-id="0fb7a-180">En el código siguiente se muestra la implementación de esta versión de este cmdlet Select-Str.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="0fb7a-181">Tenga en cuenta que este código incluye la clase de cmdlet, los métodos privados usados por el cmdlet y el código de complemento de Windows PowerShell que se usa para registrar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="0fb7a-182">Para obtener más información sobre el registro del cmdlet, consulte [compilar el cmdlet](#defining-the-cmdlet-class).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="0fb7a-183">Compilación del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0fb7a-183">Building the Cmdlet</span></span>

<span data-ttu-id="0fb7a-184">Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="0fb7a-185">Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0fb7a-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="0fb7a-186">Prueba del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0fb7a-186">Testing the Cmdlet</span></span>

<span data-ttu-id="0fb7a-187">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="0fb7a-188">El siguiente procedimiento se puede usar para probar el cmdlet Select-Str de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="0fb7a-189">Inicie Windows PowerShell y busque en el archivo de notas apariciones de líneas con la expresión ".NET".</span><span class="sxs-lookup"><span data-stu-id="0fb7a-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="0fb7a-190">Tenga en cuenta que las comillas alrededor del nombre de la ruta de acceso solo son necesarias si la ruta de acceso consta de más de una palabra.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="0fb7a-191">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="0fb7a-192">Busque en el archivo de notas las apariciones de las líneas con la palabra "sobre", seguido de cualquier otro texto.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="0fb7a-193">El parámetro `SimpleMatch` usa el valor predeterminado de `false`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="0fb7a-194">La búsqueda no distingue entre mayúsculas y minúsculas porque el parámetro `CaseSensitive` está establecido en `false`.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="0fb7a-195">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="0fb7a-196">Busque en el archivo de notas utilizando una expresión regular como modelo.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="0fb7a-197">El cmdlet busca caracteres alfabéticos y espacios en blanco entre paréntesis.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="0fb7a-198">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="0fb7a-199">Realice una búsqueda con distinción de mayúsculas y minúsculas del archivo de notas en busca de apariciones de la palabra "parámetro".</span><span class="sxs-lookup"><span data-stu-id="0fb7a-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="0fb7a-200">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="0fb7a-201">Busque en el proveedor de variables incluido en Windows PowerShell las variables que tengan valores numéricos de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="0fb7a-202">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="0fb7a-203">Use un bloque de script para buscar la cadena "pos" en el archivo SelectStrCommandSample.cs.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="0fb7a-204">La función **cmatch** para el script realiza una coincidencia de patrón sin distinción entre mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="0fb7a-205">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="0fb7a-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="0fb7a-206">Vea también</span><span class="sxs-lookup"><span data-stu-id="0fb7a-206">See Also</span></span>

[<span data-ttu-id="0fb7a-207">Cómo crear un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fb7a-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="0fb7a-208">Creación del primer cmdlet</span><span class="sxs-lookup"><span data-stu-id="0fb7a-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="0fb7a-209">Creación de un cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="0fb7a-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="0fb7a-210">Diseño del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fb7a-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="0fb7a-211">[Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0fb7a-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="0fb7a-212">[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0fb7a-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="0fb7a-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0fb7a-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
