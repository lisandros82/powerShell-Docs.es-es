---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="22281-102">Nuevas características de lenguaje de PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="22281-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="22281-103">PowerShell 5.0 presenta los siguientes nuevos elementos de lenguaje en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="22281-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="22281-104">Palabra clave class</span><span class="sxs-lookup"><span data-stu-id="22281-104">Class keyword</span></span>

<span data-ttu-id="22281-105">La palabra clave **class** define una nueva clase.</span><span class="sxs-lookup"><span data-stu-id="22281-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="22281-106">Se trata de un tipo verdadero de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22281-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="22281-107">Los miembros de clase son públicos, pero solo en el ámbito del módulo.</span><span class="sxs-lookup"><span data-stu-id="22281-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="22281-108">No puede hacer referencia al nombre de tipo como una cadena (por ejemplo, `New-Object` no funciona) y, en esta versión, no puede usar un literal de tipo (por ejemplo, `[MyClass]`) fuera del archivo de script o módulo en el que se define la clase.</span><span class="sxs-lookup"><span data-stu-id="22281-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="22281-109">Palabra clave Enum y enumeraciones</span><span class="sxs-lookup"><span data-stu-id="22281-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="22281-110">Se agregó compatibilidad con la palabra clave **enum**, que usa el delimitador de nueva línea.</span><span class="sxs-lookup"><span data-stu-id="22281-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="22281-111">Limitaciones actuales: no se puede definir un enumerador en términos propios, pero se puede inicializar una enumeración en términos de otra enumeración, tal como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="22281-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="22281-112">Además, el tipo base no se puede especificar actualmente; siempre es [int].</span><span class="sxs-lookup"><span data-stu-id="22281-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="22281-113">Un valor de enumerador debe ser una constante de tiempo de análisis; no puede establecerlo en el resultado de un comando invocado.</span><span class="sxs-lookup"><span data-stu-id="22281-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="22281-114">Las enumeraciones admiten operaciones aritméticas, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="22281-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="22281-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="22281-115">Import-DscResource</span></span>

<span data-ttu-id="22281-116">**Import-DscResource** es ahora una palabra clave dinámica verdadera.</span><span class="sxs-lookup"><span data-stu-id="22281-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="22281-117">PowerShell analiza el módulo raíz del módulo especificado y busca las clases que contienen el atributo **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="22281-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="22281-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="22281-118">ImplementingAssembly</span></span>

<span data-ttu-id="22281-119">Un nuevo campo, **ImplementingAssembly**, se agregó a ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="22281-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="22281-120">Se establece en el ensamblado dinámico creado para un módulo de script si el script define clases, o en el ensamblado cargado en el caso de los módulos binarios.</span><span class="sxs-lookup"><span data-stu-id="22281-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="22281-121">No se establece si ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="22281-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="22281-122">La reflexión en el campo **ImplementingAssembly** descubre los recursos de un módulo.</span><span class="sxs-lookup"><span data-stu-id="22281-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="22281-123">Esto significa que puede descubrir recursos escritos en PowerShell o en otros lenguajes administrados.</span><span class="sxs-lookup"><span data-stu-id="22281-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="22281-124">Campos con inicializadores:</span><span class="sxs-lookup"><span data-stu-id="22281-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="22281-125">Se admite static; funciona como un atributo, como ocurre en las restricciones de tipo, por lo que puede especificarse en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="22281-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="22281-126">Un tipo es opcional.</span><span class="sxs-lookup"><span data-stu-id="22281-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="22281-127">Todos los miembros son públicos.</span><span class="sxs-lookup"><span data-stu-id="22281-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="22281-128">Creación de instancias y constructores</span><span class="sxs-lookup"><span data-stu-id="22281-128">Constructors and instantiation</span></span>

<span data-ttu-id="22281-129">Las clases de Windows PowerShell pueden tener constructores; tienen el mismo nombre que su clase.</span><span class="sxs-lookup"><span data-stu-id="22281-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="22281-130">Los constructores se pueden sobrecargar.</span><span class="sxs-lookup"><span data-stu-id="22281-130">Constructors can be overloaded.</span></span> <span data-ttu-id="22281-131">Se admiten constructores estáticos.</span><span class="sxs-lookup"><span data-stu-id="22281-131">Static constructors are supported.</span></span> <span data-ttu-id="22281-132">Las propiedades con expresiones de inicialización se inicializan antes de ejecutar cualquier código en un constructor.</span><span class="sxs-lookup"><span data-stu-id="22281-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="22281-133">Las propiedades estáticas se inicializan antes del cuerpo de un constructor estático y las propiedades de instancia se inicializan antes del cuerpo del constructor no estático.</span><span class="sxs-lookup"><span data-stu-id="22281-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="22281-134">Actualmente no hay ninguna sintaxis para llamar a un constructor desde otro constructor (como la sintaxis ": this()" de C\#).</span><span class="sxs-lookup"><span data-stu-id="22281-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="22281-135">La solución consiste en definir un método Init común.</span><span class="sxs-lookup"><span data-stu-id="22281-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="22281-136">Las siguientes son formas de crear instancias de clases en esta versión.</span><span class="sxs-lookup"><span data-stu-id="22281-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="22281-137">Crear una instancia mediante el constructor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="22281-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="22281-138">Tenga en cuenta que New-Object no se admite en esta versión.</span><span class="sxs-lookup"><span data-stu-id="22281-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="22281-139">Llamar a un constructor con un parámetro</span><span class="sxs-lookup"><span data-stu-id="22281-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="22281-140">Pasar una matriz a un constructor con varios parámetros</span><span class="sxs-lookup"><span data-stu-id="22281-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="22281-141">En esta versión, New-Object no funciona con las clases definidas en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22281-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="22281-142">En esta versión, el nombre del tipo solo es visible léxicamente, lo que significa que no está visible fuera del módulo o el script que define la clase.</span><span class="sxs-lookup"><span data-stu-id="22281-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="22281-143">Las funciones pueden devolver instancias de una clase definida en Windows PowerShell, y las instancias funcionan bien fuera del módulo o el script.</span><span class="sxs-lookup"><span data-stu-id="22281-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="22281-144">`Get-Member -Static` enumera los constructores, para que pueda ver las sobrecargas como cualquier otro método.</span><span class="sxs-lookup"><span data-stu-id="22281-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="22281-145">El rendimiento de esta sintaxis también es considerablemente más rápido que el de New-Object.</span><span class="sxs-lookup"><span data-stu-id="22281-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="22281-146">El método seudoestático denominado **new** funciona con los tipos .NET, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="22281-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="22281-147">Ahora puede ver las sobrecargas de constructores con Get-Member, o bien como se muestra en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="22281-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="22281-148">Métodos</span><span class="sxs-lookup"><span data-stu-id="22281-148">Methods</span></span>

<span data-ttu-id="22281-149">Un método de clase de Windows PowerShell se implementa como un bloque de script que tiene solo un bloque final.</span><span class="sxs-lookup"><span data-stu-id="22281-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="22281-150">Todos los métodos son públicos.</span><span class="sxs-lookup"><span data-stu-id="22281-150">All methods are public.</span></span> <span data-ttu-id="22281-151">A continuación, se ofrece un ejemplo de definición de un método denominado **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="22281-151">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="22281-152">Invocación del método:</span><span class="sxs-lookup"><span data-stu-id="22281-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="22281-153">También se admiten los métodos sobrecargados, es decir, aquellos con el mismo nombre que un método existente, pero que se diferencian por los valores especificados.</span><span class="sxs-lookup"><span data-stu-id="22281-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="22281-154">Propiedades</span><span class="sxs-lookup"><span data-stu-id="22281-154">Properties</span></span>

<span data-ttu-id="22281-155">Todas las propiedades son públicas.</span><span class="sxs-lookup"><span data-stu-id="22281-155">All properties are public.</span></span> <span data-ttu-id="22281-156">Las propiedades requieren una nueva línea o un punto y coma.</span><span class="sxs-lookup"><span data-stu-id="22281-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="22281-157">Si no se especifica ningún tipo de objeto, el tipo de propiedad es object.</span><span class="sxs-lookup"><span data-stu-id="22281-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="22281-158">Las propiedades que usan atributos de validación o atributos de transformación de argumentos (por ejemplo, `[ValidateSet("aaa")]`) funcionan según lo esperado.</span><span class="sxs-lookup"><span data-stu-id="22281-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="22281-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="22281-159">Hidden</span></span>

<span data-ttu-id="22281-160">Se agregó la nueva palabra clave **Hidden**.</span><span class="sxs-lookup"><span data-stu-id="22281-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="22281-161">**Hidden** se puede aplicar a propiedades y métodos (incluidos constructores).</span><span class="sxs-lookup"><span data-stu-id="22281-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="22281-162">Los miembros ocultos son públicos, pero no aparecen en la salida de Get-Member salvo que se agregue el parámetro -Force.</span><span class="sxs-lookup"><span data-stu-id="22281-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="22281-163">Los miembros ocultos no se incluyen al finalizar con tabulación o usar Intellisense, salvo que la finalización se produzca en la clase que define el miembro oculto.</span><span class="sxs-lookup"><span data-stu-id="22281-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="22281-164">Un atributo nuevo, **System.Management.Automation.HiddenAttribute** se agregó para que el código de C# pueda tener la misma semántica en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22281-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="22281-165">Tipos de valor devueltos</span><span class="sxs-lookup"><span data-stu-id="22281-165">Return types</span></span>

<span data-ttu-id="22281-166">El tipo de valor devuelto es un contrato; el valor devuelto se convierte en el tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="22281-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="22281-167">Si no se especifica ningún tipo de valor devuelto, el tipo de valor devuelto es void.</span><span class="sxs-lookup"><span data-stu-id="22281-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="22281-168">No hay ningún streaming de objetos; los objetos no se pueden escribir en la canalización, ni intencionadamente ni por accidente.</span><span class="sxs-lookup"><span data-stu-id="22281-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="22281-169">Atributos</span><span class="sxs-lookup"><span data-stu-id="22281-169">Attributes</span></span>

<span data-ttu-id="22281-170">Se han agregado dos atributos nuevos: **DscResource** y **DscProperty**.</span><span class="sxs-lookup"><span data-stu-id="22281-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="22281-171">Ámbito léxico de las variables</span><span class="sxs-lookup"><span data-stu-id="22281-171">Lexical scoping of variables</span></span>

<span data-ttu-id="22281-172">A continuación, se muestra un ejemplo del funcionamiento del ámbito léxico en esta versión.</span><span class="sxs-lookup"><span data-stu-id="22281-172">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="22281-173">Acceso de un extremo a otro</span><span class="sxs-lookup"><span data-stu-id="22281-173">End-to-End Example</span></span>

<span data-ttu-id="22281-174">En el ejemplo siguiente se crean varias clases nuevas y personalizadas para implementar un lenguaje de hojas de estilo dinámico (DSL) HTML.</span><span class="sxs-lookup"><span data-stu-id="22281-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="22281-175">A continuación, el ejemplo agrega funciones auxiliares para crear tipos de elementos específicos como parte de la clase de elemento, tales como tablas y estilos de encabezado, porque los tipos no pueden usarse fuera del ámbito de un módulo.</span><span class="sxs-lookup"><span data-stu-id="22281-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
