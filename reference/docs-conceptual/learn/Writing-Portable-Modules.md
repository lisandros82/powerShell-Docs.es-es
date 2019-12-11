---
ms.date: 12/14/2018
keywords: powershell, cmdlet
title: Escritura de módulos portables
ms.openlocfilehash: 7871f524495c1ce5283b30696a24185d427edebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417649"
---
# <a name="portable-modules"></a><span data-ttu-id="99494-103">Módulos portables</span><span class="sxs-lookup"><span data-stu-id="99494-103">Portable Modules</span></span>

<span data-ttu-id="99494-104">Windows PowerShell está escrito para [.NET Framework][], mientras que PowerShell Core está escrito para [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="99494-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="99494-105">Los módulos portables son módulos que funcionan en Windows PowerShell y PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="99494-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="99494-106">Si bien .NET Framework y .NET Core son altamente compatibles, existen diferencias en las API disponibles entre los dos.</span><span class="sxs-lookup"><span data-stu-id="99494-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="99494-107">También hay diferencias en las API disponibles en Windows PowerShell y PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="99494-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="99494-108">Los módulos destinados para su uso en ambos entornos deben tener en cuenta estas diferencias.</span><span class="sxs-lookup"><span data-stu-id="99494-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="99494-109">Migración de un módulo existente</span><span class="sxs-lookup"><span data-stu-id="99494-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="99494-110">Migración de un elemento PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="99494-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="99494-111">Los complementos PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) no se admiten en PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="99494-111">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="99494-112">Sin embargo, resulta trivial convertir un PSSnapIn en un módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99494-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="99494-113">Normalmente, el código de registro del PSSnapIn se encuentra en un único archivo de código fuente de una clase que se deriva de [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="99494-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span>
<span data-ttu-id="99494-114">Quite este archivo de código fuente de la compilación; ya no es necesario.</span><span class="sxs-lookup"><span data-stu-id="99494-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="99494-115">Use [New-ModuleManifest][] para crear un nuevo manifiesto de módulo que reemplace la necesidad del código de registro del PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="99494-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="99494-116">Algunos de los valores del complemento **PSSnapIn** (como la **descripción**) se pueden reutilizar en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="99494-116">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="99494-117">La propiedad **RootModule** del manifiesto del módulo debe establecerse en el nombre del ensamblado (dll) que implementa los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="99494-117">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="99494-118">Analizador de portabilidad de .NET (también conocido como APIPort)</span><span class="sxs-lookup"><span data-stu-id="99494-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="99494-119">Para migrar los módulos escritos para Windows PowerShell para que funcionen con PowerShell Core, empiece con el [analizador de portabilidad de .NET][].</span><span class="sxs-lookup"><span data-stu-id="99494-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="99494-120">Ejecute esta herramienta en su ensamblado compilado para determinar si las API de .NET utilizadas en el módulo son compatibles con .NET Framework, .NET Core y otros entornos de ejecución de .NET.</span><span class="sxs-lookup"><span data-stu-id="99494-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="99494-121">La herramienta sugiere API alternativas si existen.</span><span class="sxs-lookup"><span data-stu-id="99494-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="99494-122">En caso contrario, es posible que deba agregar [comprobaciones del entorno de ejecución][] y restringir las funciones no disponibles en los entornos de ejecución específicos.</span><span class="sxs-lookup"><span data-stu-id="99494-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="99494-123">Creación de un módulo</span><span class="sxs-lookup"><span data-stu-id="99494-123">Creating a New Module</span></span>

<span data-ttu-id="99494-124">Si crea un nuevo módulo, la recomendación es que use la [CLI de .NET][].</span><span class="sxs-lookup"><span data-stu-id="99494-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="99494-125">Instalación de la plantilla del módulo de PowerShell estándar</span><span class="sxs-lookup"><span data-stu-id="99494-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="99494-126">Una vez que la CLI de .NET esté instalada, instale una biblioteca de plantillas para generar un módulo de PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="99494-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="99494-127">El módulo será compatible con Windows PowerShell, PowerShell Core, Windows, Linux y macOS.</span><span class="sxs-lookup"><span data-stu-id="99494-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="99494-128">En el ejemplo siguiente se muestra cómo instalar la plantilla:</span><span class="sxs-lookup"><span data-stu-id="99494-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="99494-129">Creación de un proyecto de módulo</span><span class="sxs-lookup"><span data-stu-id="99494-129">Creating a New Module Project</span></span>

<span data-ttu-id="99494-130">Después de instalar la plantilla, puede crear un nuevo proyecto de módulo de PowerShell con esa plantilla.</span><span class="sxs-lookup"><span data-stu-id="99494-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="99494-131">En este ejemplo, el módulo de ejemplo se denomina "myModule".</span><span class="sxs-lookup"><span data-stu-id="99494-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="99494-132">Compilación del módulo</span><span class="sxs-lookup"><span data-stu-id="99494-132">Building the Module</span></span>

<span data-ttu-id="99494-133">Use los comandos CLI de .NET estándar para compilar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="99494-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="99494-134">Prueba del módulo</span><span class="sxs-lookup"><span data-stu-id="99494-134">Testing the Module</span></span>

<span data-ttu-id="99494-135">Después de compilar el módulo, puede importarlo y ejecutar el cmdlet de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="99494-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="99494-136">Las secciones siguientes describen en detalle algunas de las tecnologías usadas por esta plantilla.</span><span class="sxs-lookup"><span data-stu-id="99494-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="99494-137">Biblioteca de .NET Standard</span><span class="sxs-lookup"><span data-stu-id="99494-137">.NET Standard Library</span></span>

<span data-ttu-id="99494-138">[.NET standard][] es una especificación formal de las API de .NET que están disponibles en todas las implementaciones de. NET.</span><span class="sxs-lookup"><span data-stu-id="99494-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="99494-139">El código administrado destinado a .NET Standard funciona con las versiones .NET Framework y .NET Core que son compatibles con esa versión de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="99494-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="99494-140">Aunque puede existir una API en .NET Standard, la implementación de la API de .NET Core puede producir un `PlatformNotSupportedException` en el entorno de ejecución; así pues, para comprobar la compatibilidad con Windows PowerShell y PowerShell Core, el procedimiento recomendado es ejecutar pruebas para el módulo en ambos entornos.</span><span class="sxs-lookup"><span data-stu-id="99494-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="99494-141">También debe ejecutar las pruebas en Linux y macOS si el módulo está pensado para ser multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="99494-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="99494-142">Destinarlo a .NET Standard ayuda a garantizar que, a medida que evoluciona el módulo, las API incompatibles no se introduzcan involuntariamente en el módulo.</span><span class="sxs-lookup"><span data-stu-id="99494-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="99494-143">Las incompatibilidades se detectan en tiempo de compilación en lugar de en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="99494-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="99494-144">Sin embargo, no es necesario que un módulo tenga como destino .NET Standard para que funcione con Windows PowerShell y PowerShell Core, siempre que use API compatibles.</span><span class="sxs-lookup"><span data-stu-id="99494-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="99494-145">El lenguaje intermedio (IL) es compatible entre los dos tiempos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="99494-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="99494-146">Puede tener como destino .NET Framework 4.6.1, que es compatible con .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="99494-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="99494-147">Si no usa las API fuera de .NET Standard 2.0, el módulo funciona con PowerShell Core 6 sin volver a compilar.</span><span class="sxs-lookup"><span data-stu-id="99494-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="99494-148">Biblioteca de PowerShell estándar</span><span class="sxs-lookup"><span data-stu-id="99494-148">PowerShell Standard Library</span></span>

<span data-ttu-id="99494-149">La biblioteca de [PowerShell estándar][] es una especificación formal de las API de PowerShell disponibles en todas las versiones de PowerShell que sean superiores o iguales a la versión de ese estándar.</span><span class="sxs-lookup"><span data-stu-id="99494-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="99494-150">Por ejemplo, [PowerShell estándar 5.1][] es compatible con Windows PowerShell 5.1 y PowerShell Core 6.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="99494-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="99494-151">Se recomienda que compile el módulo mediante la biblioteca estándar de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99494-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="99494-152">La biblioteca garantiza que las API están disponibles y se implementan en Windows PowerShell y PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="99494-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="99494-153">PowerShell estándar está concebido para que sea compatible siempre con versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="99494-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="99494-154">Un módulo compilado con la biblioteca de PowerShell estándar 5.1 siempre será compatible con versiones futuras de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99494-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="99494-155">Manifiesto de módulo</span><span class="sxs-lookup"><span data-stu-id="99494-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="99494-156">Indicación de la compatibilidad con Windows PowerShell y PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="99494-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="99494-157">Después de comprobar que el módulo funciona con Windows PowerShell y PowerShell Core, el manifiesto del módulo debe indicar explícitamente la compatibilidad mediante el uso de la propiedad [CompatiblePSEditions][].</span><span class="sxs-lookup"><span data-stu-id="99494-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="99494-158">Un valor de `Desktop` significa que el módulo es compatible con Windows PowerShell, mientras que un valor de `Core` significa que el módulo es compatible con PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="99494-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="99494-159">La inclusión de `Desktop` y `Core` significa que el módulo es compatible con Windows PowerShell y PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="99494-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="99494-160">`Core` no significa automáticamente que el módulo sea compatible con Windows, Linux y macOS.</span><span class="sxs-lookup"><span data-stu-id="99494-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="99494-161">La propiedad **CompatiblePSEditions** se introdujo en PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="99494-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="99494-162">Los manifiestos de módulo que usan la propiedad **CompatiblePSEditions** no se pueden cargar en las versiones anteriores de PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="99494-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="99494-163">Indicación de la compatibilidad del SO</span><span class="sxs-lookup"><span data-stu-id="99494-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="99494-164">En primer lugar, valide que el módulo funciona en Linux y macOS.</span><span class="sxs-lookup"><span data-stu-id="99494-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="99494-165">A continuación, indique la compatibilidad con esos sistemas operativos en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="99494-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="99494-166">Esto facilita a los usuarios encontrar el módulo para su sistema operativo cuando se publican en la [Galería de PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="99494-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="99494-167">En el manifiesto del módulo, la propiedad `PrivateData` tiene una subpropiedad `PSData`.</span><span class="sxs-lookup"><span data-stu-id="99494-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="99494-168">La propiedad `Tags` opcional de `PSData` toma una matriz de valores que se muestran en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99494-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="99494-169">La Galería de PowerShell admite los siguientes valores de compatibilidad:</span><span class="sxs-lookup"><span data-stu-id="99494-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="99494-170">Etiqueta</span><span class="sxs-lookup"><span data-stu-id="99494-170">Tag</span></span>               | <span data-ttu-id="99494-171">Descripción</span><span class="sxs-lookup"><span data-stu-id="99494-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="99494-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="99494-172">PSEdition_Core</span></span>    | <span data-ttu-id="99494-173">Compatible con PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="99494-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="99494-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="99494-174">PSEdition_Desktop</span></span> | <span data-ttu-id="99494-175">Compatible con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99494-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="99494-176">Windows</span><span class="sxs-lookup"><span data-stu-id="99494-176">Windows</span></span>           | <span data-ttu-id="99494-177">Compatible con Windows</span><span class="sxs-lookup"><span data-stu-id="99494-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="99494-178">Linux</span><span class="sxs-lookup"><span data-stu-id="99494-178">Linux</span></span>             | <span data-ttu-id="99494-179">Compatible con Linux (ninguna distribución específica)</span><span class="sxs-lookup"><span data-stu-id="99494-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="99494-180">macOS</span><span class="sxs-lookup"><span data-stu-id="99494-180">macOS</span></span>             | <span data-ttu-id="99494-181">Compatible con macOS</span><span class="sxs-lookup"><span data-stu-id="99494-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="99494-182">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99494-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Comprobaciones del entorno de ejecución]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[CLI de .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell estándar]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell estándar 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galería de PowerShell]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[Analizador de portabilidad de .NET]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
