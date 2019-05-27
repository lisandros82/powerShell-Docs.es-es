---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Creación de tipos personalizados mediante clases de PowerShell
ms.openlocfilehash: 0dd5bbaca50abb746e15a7bb64a706c7eceee905
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855540"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Creación de tipos personalizados mediante clases de PowerShell

PowerShell 5.0 agregó la capacidad de definir clases y otros tipos definidos por el usuario con semántica y sintaxis formal, de manera similar a otros lenguajes de programación orientados a objetos. El objetivo es permitir a los desarrolladores y profesionales de TI adoptar PowerShell para una gama más amplia de casos de uso, simplificar el desarrollo de artefactos de PowerShell (como recursos de DSC) y acelerar la cobertura de las superficies de administración.

## <a name="supported-scenarios-in-this-release"></a>Escenarios admitidos en esta versión

- Definición de recursos de DSC y sus tipos asociados mediante el lenguaje de PowerShell.
- Definición de tipos personalizados en PowerShell mediante construcciones de programación conocidas orientadas a objetos, tales como clases, propiedades, métodos, etc.
- Compatibilidad de herencia con la clase de PowerShell y el recurso de DSC basado en la clase.
- Depuración de tipos mediante el lenguaje de PowerShell.
- Generación y control de excepciones mediante mecanismos formales y en el nivel correcto.

# <a name="declare-base-class"></a>Declarar una clase base

Puede declarar una clase de PowerShell como un tipo base para otra clase de PowerShell.

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

También puede usar los tipos de .NET Framework existentes como clases base:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

# <a name="call-base-class-constructor"></a>Llamar al constructor de clase base

Para llamar a un constructor de clase base desde una subclase, use la palabra clave **base**:

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

Si una clase base tiene un constructor predeterminado (sin parámetros), se puede omitir una llamada explícita al constructor:

```powershell
class C : B
{
    C([int]$c) {}
}
```

# <a name="call-base-class-method"></a>Llamar al método de clase base

Puede invalidar los métodos existentes en las subclases. Para ello, declare métodos con el mismo nombre y la misma firma:

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

Para llamar a métodos de clase base desde implementaciones reemplazadas, conviértalos a la clase base (`[baseClass]$this`) al invocarlos:

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

Todos los métodos de PowerShell son virtuales. Puede ocultar los métodos no virtuales de .NET en una subclase usando la misma sintaxis que para un reemplazo, mediante la declaración de métodos con el mismo nombre y la misma firma.

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

# <a name="declare-implemented-interface"></a>Declarar la interfaz implementada

Puede declarar interfaces implementadas después de los tipos base o inmediatamente después de dos puntos (:) si no existe ningún tipo base especificado. Separe todos los nombres de tipo con comas. Es similar a la sintaxis de C#.

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

# <a name="new-language-features-in-powershell-50"></a>Nuevas características de lenguaje de PowerShell 5.0

PowerShell 5.0 presenta los siguientes nuevos elementos de lenguaje en PowerShell:

## <a name="class-keyword"></a>Palabra clave class

La palabra clave `class` define una nueva clase. Se trata de un tipo verdadero de .NET Framework. Los miembros de clase son públicos, pero solo en el ámbito del módulo. No puede hacer referencia al nombre de tipo como una cadena (por ejemplo, `New-Object` no funciona) y, en esta versión, no puede usar un literal de tipo (por ejemplo, `[MyClass]`) fuera del archivo de script o módulo en el que se define la clase.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Palabra clave Enum y enumeraciones

Se agregó compatibilidad con la palabra clave `enum`, que usa el delimitador de nueva línea. No es posible definir actualmente un enumerador en términos propios. Sin embargo, puede inicializar una enumeración en términos de otra enumeración, tal como se muestra en el ejemplo siguiente. Además, el tipo base no se puede especificar, porque siempre es `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Un valor de enumerador debe ser una constante de tiempo de análisis. No puede establecerlo en el resultado de un comando invocado.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Las enumeraciones admiten operaciones aritméticas, como se muestra en el ejemplo siguiente.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` ahora es una palabra clave dinámica verdadera. PowerShell analiza el módulo raíz del módulo especificado y busca las clases que contienen el atributo **DscResource**.

## <a name="implementingassembly"></a>ImplementingAssembly

Un campo nuevo, **ImplementingAssembly**, se agregó a **ModuleInfo**. Se establece en el ensamblado dinámico creado para un módulo de script si el script define clases, o en el ensamblado cargado en el caso de los módulos binarios. No se establece si **ModuleType** es **Manifest**.

La reflexión en el campo **ImplementingAssembly** descubre los recursos de un módulo. Esto significa que puede descubrir recursos escritos en PowerShell o en otros lenguajes administrados.

Campos con inicializadores:

```powershell
[int] $i = 5
```

`Static` es compatible. Funciona como atributo, al igual que las restricciones de tipo. Se puede especificar en cualquier orden.

```powershell
static [int] $count = 0
```

Un tipo es opcional.

```powershell
$s = "hello"
```

Todos los miembros son públicos.

## <a name="constructors-and-instantiation"></a>Creación de instancias y constructores

Las clases de PowerShell pueden tener constructores. Tienen el mismo nombre que su clase. Los constructores se pueden sobrecargar. Se admiten constructores estáticos. Las propiedades con expresiones de inicialización se inicializan antes de ejecutar cualquier código en un constructor. Las propiedades estáticas se inicializan antes del cuerpo de un constructor estático y las propiedades de instancia se inicializan antes del cuerpo del constructor no estático. Actualmente no hay ninguna sintaxis para llamar a un constructor desde otro constructor (como la sintaxis ": this()" de C\#). La solución consiste en definir un método `Init()` común.

### <a name="creating-instances"></a>Creación de instancias

> [!NOTE]
> En PowerShell 5.0, `New-Object` no funciona con las clases definidas en PowerShell. Además, el nombre del tipo solo es visible léxicamente, lo que significa que no está visible fuera del módulo o el script que define la clase. Las funciones deben devolver instancias de una clase definida en PowerShell. Esas instancias funcionan fuera del módulo o del script.

1. Crear una instancia mediante el constructor predeterminado.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Llamar a un constructor con un parámetro

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Pasar una matriz a un constructor con varios parámetros.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

El método seudoestático `new()` funciona con los tipos .NET, como se muestra en el ejemplo siguiente.

```powershell
[hashtable]::new()
```

### <a name="discovering-constructors"></a>Detección de constructores

Ahora puede ver las sobrecargas de constructores con `Get-Member`, o bien como se muestra en este ejemplo:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` enumera los constructores, para que pueda ver las sobrecargas como cualquier otro método. El rendimiento de esta sintaxis también es considerablemente más rápido que el de `New-Object`.

## <a name="methods"></a>Métodos

Un método de clase de PowerShell se implementa como un **bloque de script** que tiene solo un bloque final. Todos los métodos son públicos. A continuación, se ofrece un ejemplo de definición de un método denominado **DoSomething**.

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

Invocación del método:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

También se admiten los métodos sobrecargados.

## <a name="properties"></a>Propiedades

Todas las propiedades son públicas. Las propiedades requieren una nueva línea o un punto y coma. Si no se especifica ningún tipo de objeto, el tipo de propiedad es object.

Las propiedades que usan atributos de validación o de transformación de argumentos (por ejemplo, `[ValidateSet("aaa")]`) funcionan según lo esperado.

## <a name="hidden"></a>Hidden

Se agregó una nueva palabra clave, `Hidden`. `Hidden` se puede aplicar a propiedades y métodos (incluidos constructores).

Los miembros ocultos son públicos, pero no aparecen en la salida de `Get-Member` salvo que se agregue el parámetro -Force. Los miembros ocultos no se incluyen al finalizar con tabulación o usar Intellisense, salvo que la finalización se produzca en la clase que define el miembro oculto.

Un atributo nuevo, **System.Management.Automation.HiddenAttribute** se agregó para que el código de C\# pueda tener la misma semántica en PowerShell.

## <a name="return-types"></a>Tipos de valor devueltos

El tipo de valor devuelto es un contrato. El valor devuelto se convierte al tipo esperado. Si no se especifica ningún tipo de valor devuelto, el tipo de valor devuelto es **void**. No hay ninguna transmisión de objetos. Los objetos no se pueden escribir en la canalización, ni de manera intencionada ni por accidente.

## <a name="attributes"></a>Atributos

Se han agregado dos atributos nuevos: **DscResource** y **DscProperty**.

## <a name="lexical-scoping-of-variables"></a>Ámbito léxico de las variables

A continuación, se muestra un ejemplo del funcionamiento del ámbito léxico en esta versión.

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

## <a name="end-to-end-example"></a>Acceso de un extremo a otro

En el ejemplo siguiente se crean algunas clases personalizadas para implementar un lenguaje de hojas de estilo dinámico (DSL) HTML. A continuación, el ejemplo agrega funciones del asistente para crear tipos de elementos específicos como parte de la clase de elemento, tales como tablas y estilos de encabezado, porque los tipos no pueden usarse fuera del ámbito de un módulo.

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
