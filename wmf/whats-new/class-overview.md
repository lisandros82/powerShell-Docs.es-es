---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Creación de tipos personalizados mediante clases de PowerShell
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470937"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="de9a3-103">Creación de tipos personalizados mediante clases de PowerShell</span><span class="sxs-lookup"><span data-stu-id="de9a3-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="de9a3-104">PowerShell 5.0 agregó la capacidad de definir clases y otros tipos definidos por el usuario con semántica y sintaxis formal, de manera similar a otros lenguajes de programación orientados a objetos.</span><span class="sxs-lookup"><span data-stu-id="de9a3-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="de9a3-105">El objetivo es permitir a los desarrolladores y profesionales de TI adoptar PowerShell para una gama más amplia de casos de uso, simplificar el desarrollo de artefactos de PowerShell (como recursos de DSC) y acelerar la cobertura de las superficies de administración.</span><span class="sxs-lookup"><span data-stu-id="de9a3-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="de9a3-106">Escenarios admitidos en esta versión</span><span class="sxs-lookup"><span data-stu-id="de9a3-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="de9a3-107">Definición de recursos de DSC y sus tipos asociados mediante el lenguaje de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9a3-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="de9a3-108">Definición de tipos personalizados en PowerShell mediante construcciones de programación conocidas orientadas a objetos, tales como clases, propiedades, métodos, etc.</span><span class="sxs-lookup"><span data-stu-id="de9a3-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="de9a3-109">Compatibilidad de herencia con la clase de PowerShell y el recurso de DSC basado en la clase.</span><span class="sxs-lookup"><span data-stu-id="de9a3-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="de9a3-110">Depuración de tipos mediante el lenguaje de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9a3-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="de9a3-111">Generación y control de excepciones mediante mecanismos formales y en el nivel correcto.</span><span class="sxs-lookup"><span data-stu-id="de9a3-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="de9a3-112">Declarar una clase base</span><span class="sxs-lookup"><span data-stu-id="de9a3-112">Declare Base Class</span></span>

<span data-ttu-id="de9a3-113">Puede declarar una clase de PowerShell como un tipo base para otra clase de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9a3-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="de9a3-114">También puede usar los tipos de .NET Framework existentes como clases base:</span><span class="sxs-lookup"><span data-stu-id="de9a3-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="de9a3-115">Llamar al constructor de clase base</span><span class="sxs-lookup"><span data-stu-id="de9a3-115">Call Base Class Constructor</span></span>

<span data-ttu-id="de9a3-116">Para llamar a un constructor de clase base desde una subclase, use la palabra clave **base**:</span><span class="sxs-lookup"><span data-stu-id="de9a3-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="de9a3-117">Si una clase base tiene un constructor predeterminado (sin parámetros), se puede omitir una llamada explícita al constructor:</span><span class="sxs-lookup"><span data-stu-id="de9a3-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="de9a3-118">Llamar al método de clase base</span><span class="sxs-lookup"><span data-stu-id="de9a3-118">Call Base Class Method</span></span>

<span data-ttu-id="de9a3-119">Puede invalidar los métodos existentes en las subclases.</span><span class="sxs-lookup"><span data-stu-id="de9a3-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="de9a3-120">Para ello, declare métodos con el mismo nombre y la misma firma:</span><span class="sxs-lookup"><span data-stu-id="de9a3-120">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="de9a3-121">Para llamar a métodos de clase base desde implementaciones reemplazadas, conviértalos a la clase base (`[baseClass]$this`) al invocarlos:</span><span class="sxs-lookup"><span data-stu-id="de9a3-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="de9a3-122">Todos los métodos de PowerShell son virtuales.</span><span class="sxs-lookup"><span data-stu-id="de9a3-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="de9a3-123">Puede ocultar los métodos no virtuales de .NET en una subclase usando la misma sintaxis que para un reemplazo, mediante la declaración de métodos con el mismo nombre y la misma firma.</span><span class="sxs-lookup"><span data-stu-id="de9a3-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a><span data-ttu-id="de9a3-124">Declarar la interfaz implementada</span><span class="sxs-lookup"><span data-stu-id="de9a3-124">Declare Implemented Interface</span></span>

<span data-ttu-id="de9a3-125">Puede declarar interfaces implementadas después de los tipos base o inmediatamente después de dos puntos (:) si no existe ningún tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="de9a3-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="de9a3-126">Separe todos los nombres de tipo con comas.</span><span class="sxs-lookup"><span data-stu-id="de9a3-126">Separate all type names by using commas.</span></span> <span data-ttu-id="de9a3-127">Es similar a la sintaxis de C#.</span><span class="sxs-lookup"><span data-stu-id="de9a3-127">It's similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="de9a3-128">Nuevas características de lenguaje de PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="de9a3-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="de9a3-129">PowerShell 5.0 presenta los siguientes nuevos elementos de lenguaje en PowerShell:</span><span class="sxs-lookup"><span data-stu-id="de9a3-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="de9a3-130">Palabra clave class</span><span class="sxs-lookup"><span data-stu-id="de9a3-130">Class keyword</span></span>

<span data-ttu-id="de9a3-131">La palabra clave `class` define una nueva clase.</span><span class="sxs-lookup"><span data-stu-id="de9a3-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="de9a3-132">Se trata de un tipo verdadero de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de9a3-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="de9a3-133">Los miembros de clase son públicos, pero solo en el ámbito del módulo.</span><span class="sxs-lookup"><span data-stu-id="de9a3-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="de9a3-134">No puede hacer referencia al nombre de tipo como una cadena (por ejemplo, `New-Object` no funciona) y, en esta versión, no puede usar un literal de tipo (por ejemplo, `[MyClass]`) fuera del archivo de script o módulo en el que se define la clase.</span><span class="sxs-lookup"><span data-stu-id="de9a3-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="de9a3-135">Palabra clave Enum y enumeraciones</span><span class="sxs-lookup"><span data-stu-id="de9a3-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="de9a3-136">Se agregó compatibilidad con la palabra clave `enum`, que usa el delimitador de nueva línea.</span><span class="sxs-lookup"><span data-stu-id="de9a3-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="de9a3-137">No es posible definir actualmente un enumerador en términos propios.</span><span class="sxs-lookup"><span data-stu-id="de9a3-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="de9a3-138">Sin embargo, puede inicializar una enumeración en términos de otra enumeración, tal como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="de9a3-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="de9a3-139">Además, el tipo base no se puede especificar, porque siempre es `[int]`.</span><span class="sxs-lookup"><span data-stu-id="de9a3-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="de9a3-140">Un valor de enumerador debe ser una constante de tiempo de análisis.</span><span class="sxs-lookup"><span data-stu-id="de9a3-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="de9a3-141">No puede establecerlo en el resultado de un comando invocado.</span><span class="sxs-lookup"><span data-stu-id="de9a3-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="de9a3-142">Las enumeraciones admiten operaciones aritméticas, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="de9a3-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="de9a3-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="de9a3-143">Import-DscResource</span></span>

<span data-ttu-id="de9a3-144">`Import-DscResource` ahora es una palabra clave dinámica verdadera.</span><span class="sxs-lookup"><span data-stu-id="de9a3-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="de9a3-145">PowerShell analiza el módulo raíz del módulo especificado y busca las clases que contienen el atributo **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="de9a3-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="de9a3-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="de9a3-146">ImplementingAssembly</span></span>

<span data-ttu-id="de9a3-147">Un campo nuevo, **ImplementingAssembly**, se agregó a **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="de9a3-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="de9a3-148">Se establece en el ensamblado dinámico creado para un módulo de script si el script define clases, o en el ensamblado cargado en el caso de los módulos binarios.</span><span class="sxs-lookup"><span data-stu-id="de9a3-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="de9a3-149">No se establece si **ModuleType** es **Manifest**.</span><span class="sxs-lookup"><span data-stu-id="de9a3-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="de9a3-150">La reflexión en el campo **ImplementingAssembly** descubre los recursos de un módulo.</span><span class="sxs-lookup"><span data-stu-id="de9a3-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="de9a3-151">Esto significa que puede descubrir recursos escritos en PowerShell o en otros lenguajes administrados.</span><span class="sxs-lookup"><span data-stu-id="de9a3-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="de9a3-152">Campos con inicializadores:</span><span class="sxs-lookup"><span data-stu-id="de9a3-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="de9a3-153">`Static` es compatible.</span><span class="sxs-lookup"><span data-stu-id="de9a3-153">`Static` is supported.</span></span> <span data-ttu-id="de9a3-154">Funciona como atributo, al igual que las restricciones de tipo.</span><span class="sxs-lookup"><span data-stu-id="de9a3-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="de9a3-155">Se puede especificar en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="de9a3-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="de9a3-156">Un tipo es opcional.</span><span class="sxs-lookup"><span data-stu-id="de9a3-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="de9a3-157">Todos los miembros son públicos.</span><span class="sxs-lookup"><span data-stu-id="de9a3-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="de9a3-158">Creación de instancias y constructores</span><span class="sxs-lookup"><span data-stu-id="de9a3-158">Constructors and instantiation</span></span>

<span data-ttu-id="de9a3-159">Las clases de PowerShell pueden tener constructores.</span><span class="sxs-lookup"><span data-stu-id="de9a3-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="de9a3-160">Tienen el mismo nombre que su clase.</span><span class="sxs-lookup"><span data-stu-id="de9a3-160">They have the same name as their class.</span></span> <span data-ttu-id="de9a3-161">Los constructores se pueden sobrecargar.</span><span class="sxs-lookup"><span data-stu-id="de9a3-161">Constructors can be overloaded.</span></span> <span data-ttu-id="de9a3-162">Se admiten constructores estáticos.</span><span class="sxs-lookup"><span data-stu-id="de9a3-162">Static constructors are supported.</span></span> <span data-ttu-id="de9a3-163">Las propiedades con expresiones de inicialización se inicializan antes de ejecutar cualquier código en un constructor.</span><span class="sxs-lookup"><span data-stu-id="de9a3-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="de9a3-164">Las propiedades estáticas se inicializan antes del cuerpo de un constructor estático y las propiedades de instancia se inicializan antes del cuerpo del constructor no estático.</span><span class="sxs-lookup"><span data-stu-id="de9a3-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="de9a3-165">Actualmente no hay ninguna sintaxis para llamar a un constructor desde otro constructor (como la sintaxis ": this()" de C\#).</span><span class="sxs-lookup"><span data-stu-id="de9a3-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="de9a3-166">La solución consiste en definir un método `Init()` común.</span><span class="sxs-lookup"><span data-stu-id="de9a3-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="de9a3-167">Creación de instancias</span><span class="sxs-lookup"><span data-stu-id="de9a3-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="de9a3-168">En PowerShell 5.0, `New-Object` no funciona con las clases definidas en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9a3-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="de9a3-169">Además, el nombre del tipo solo es visible léxicamente, lo que significa que no está visible fuera del módulo o el script que define la clase.</span><span class="sxs-lookup"><span data-stu-id="de9a3-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="de9a3-170">Las funciones deben devolver instancias de una clase definida en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9a3-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="de9a3-171">Esas instancias funcionan fuera del módulo o del script.</span><span class="sxs-lookup"><span data-stu-id="de9a3-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="de9a3-172">Crear una instancia mediante el constructor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="de9a3-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="de9a3-173">Llamar a un constructor con un parámetro</span><span class="sxs-lookup"><span data-stu-id="de9a3-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="de9a3-174">Pasar una matriz a un constructor con varios parámetros.</span><span class="sxs-lookup"><span data-stu-id="de9a3-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="de9a3-175">El método seudoestático `new()` funciona con los tipos .NET, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="de9a3-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="de9a3-176">Detección de constructores</span><span class="sxs-lookup"><span data-stu-id="de9a3-176">Discovering constructors</span></span>

<span data-ttu-id="de9a3-177">Ahora puede ver las sobrecargas de constructores con `Get-Member`, o bien como se muestra en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="de9a3-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="de9a3-178">`Get-Member -Static` enumera los constructores, para que pueda ver las sobrecargas como cualquier otro método.</span><span class="sxs-lookup"><span data-stu-id="de9a3-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="de9a3-179">El rendimiento de esta sintaxis también es considerablemente más rápido que el de `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="de9a3-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="de9a3-180">Métodos</span><span class="sxs-lookup"><span data-stu-id="de9a3-180">Methods</span></span>

<span data-ttu-id="de9a3-181">Un método de clase de PowerShell se implementa como un **bloque de script** que tiene solo un bloque final.</span><span class="sxs-lookup"><span data-stu-id="de9a3-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="de9a3-182">Todos los métodos son públicos.</span><span class="sxs-lookup"><span data-stu-id="de9a3-182">All methods are public.</span></span> <span data-ttu-id="de9a3-183">A continuación, se ofrece un ejemplo de definición de un método denominado **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="de9a3-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="de9a3-184">Invocación del método:</span><span class="sxs-lookup"><span data-stu-id="de9a3-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="de9a3-185">También se admiten los métodos sobrecargados.</span><span class="sxs-lookup"><span data-stu-id="de9a3-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="de9a3-186">Propiedades</span><span class="sxs-lookup"><span data-stu-id="de9a3-186">Properties</span></span>

<span data-ttu-id="de9a3-187">Todas las propiedades son públicas.</span><span class="sxs-lookup"><span data-stu-id="de9a3-187">All properties are public.</span></span> <span data-ttu-id="de9a3-188">Las propiedades requieren una nueva línea o un punto y coma.</span><span class="sxs-lookup"><span data-stu-id="de9a3-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="de9a3-189">Si no se especifica ningún tipo de objeto, el tipo de propiedad es object.</span><span class="sxs-lookup"><span data-stu-id="de9a3-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="de9a3-190">Las propiedades que usan atributos de validación o de transformación de argumentos (por ejemplo, `[ValidateSet("aaa")]`) funcionan según lo esperado.</span><span class="sxs-lookup"><span data-stu-id="de9a3-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="de9a3-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="de9a3-191">Hidden</span></span>

<span data-ttu-id="de9a3-192">Se agregó una nueva palabra clave, `Hidden`.</span><span class="sxs-lookup"><span data-stu-id="de9a3-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="de9a3-193">`Hidden` se puede aplicar a propiedades y métodos (incluidos constructores).</span><span class="sxs-lookup"><span data-stu-id="de9a3-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="de9a3-194">Los miembros ocultos son públicos, pero no aparecen en la salida de `Get-Member`, salvo que se agregue el parámetro `-Force`.</span><span class="sxs-lookup"><span data-stu-id="de9a3-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="de9a3-195">Los miembros ocultos no se incluyen al finalizar con tabulación o usar Intellisense, salvo que la finalización se produzca en la clase que define el miembro oculto.</span><span class="sxs-lookup"><span data-stu-id="de9a3-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="de9a3-196">Un atributo nuevo, **System.Management.Automation.HiddenAttribute** se agregó para que el código de C\# pueda tener la misma semántica en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9a3-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="de9a3-197">Tipos de valor devueltos</span><span class="sxs-lookup"><span data-stu-id="de9a3-197">Return types</span></span>

<span data-ttu-id="de9a3-198">El tipo de valor devuelto es un contrato.</span><span class="sxs-lookup"><span data-stu-id="de9a3-198">Return type is a contract.</span></span> <span data-ttu-id="de9a3-199">El valor devuelto se convierte al tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="de9a3-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="de9a3-200">Si no se especifica ningún tipo de valor devuelto, el tipo de valor devuelto es **void**.</span><span class="sxs-lookup"><span data-stu-id="de9a3-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="de9a3-201">No hay ninguna transmisión de objetos.</span><span class="sxs-lookup"><span data-stu-id="de9a3-201">There is no streaming of objects.</span></span> <span data-ttu-id="de9a3-202">Los objetos no se pueden escribir en la canalización, ni de manera intencionada ni por accidente.</span><span class="sxs-lookup"><span data-stu-id="de9a3-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="de9a3-203">Atributos</span><span class="sxs-lookup"><span data-stu-id="de9a3-203">Attributes</span></span>

<span data-ttu-id="de9a3-204">Se han agregado dos atributos nuevos: **DscResource** y **DscProperty**.</span><span class="sxs-lookup"><span data-stu-id="de9a3-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="de9a3-205">Ámbito léxico de las variables</span><span class="sxs-lookup"><span data-stu-id="de9a3-205">Lexical scoping of variables</span></span>

<span data-ttu-id="de9a3-206">A continuación, se muestra un ejemplo del funcionamiento del ámbito léxico en esta versión.</span><span class="sxs-lookup"><span data-stu-id="de9a3-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="de9a3-207">Acceso de un extremo a otro</span><span class="sxs-lookup"><span data-stu-id="de9a3-207">End-to-End Example</span></span>

<span data-ttu-id="de9a3-208">En el ejemplo siguiente se crean algunas clases personalizadas para implementar un lenguaje de hojas de estilo dinámico (DSL) HTML.</span><span class="sxs-lookup"><span data-stu-id="de9a3-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="de9a3-209">A continuación, el ejemplo agrega funciones del asistente para crear tipos de elementos específicos como parte de la clase de elemento, tales como tablas y estilos de encabezado, porque los tipos no pueden usarse fuera del ámbito de un módulo.</span><span class="sxs-lookup"><span data-stu-id="de9a3-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
# These are required because types aren't visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
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
