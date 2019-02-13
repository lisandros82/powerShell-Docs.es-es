---
ms.date: 12/14/2018
keywords: powershell, cmdlet
title: Escritura de módulos portables
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682555"
---
# <a name="portable-modules"></a>Módulos portables

Windows PowerShell está escrito para [.NET Framework][] mientras se escribe PowerShell Core para [.NET Core][]. Módulos portátiles son módulos que funcionan en Windows PowerShell y PowerShell Core. Aunque son altamente compatible con .NET Framework y .NET Core, hay diferencias en las API disponibles entre los dos. También hay diferencias en las API disponibles en Windows PowerShell y PowerShell Core. Diseñado para utilizarse en ambos entornos de módulos se deben tener en cuenta estas diferencias.

## <a name="porting-an-existing-module"></a>Migración de un módulo existente

### <a name="porting-a-pssnapin"></a>Trasladar un PSSnapIn

PowerShell SnapIns (PSSnapIn) no se admiten en PowerShell Core. Sin embargo, resulta trivial para convertir un PSSnapIn en un módulo de PowerShell. Normalmente, el código de registro PSSnapIn está en un archivo de origen único de una clase que derive de [PSSnapIn][]. Quitar este archivo de código fuente de la compilación; ya no es necesario.

Use [New-ModuleManifest][] para crear un nuevo manifiesto de módulo que no es necesario el código de registro PSSnapIn. Algunos de los valores de la PSSnapIn (como la descripción) se pueden reutilizar en el manifiesto del módulo.

El `RootModule` propiedad en el manifiesto del módulo debe establecerse en el nombre del ensamblado (dll) que implementa los cmdlets.

### <a name="the-net-portability-analyzer-aka-apiport"></a>El analizador de portabilidad de .NET (también conocido como APIPort)

Para los módulos de puerto escritos para que Windows PowerShell trabajar con PowerShell Core, comience con la [Analizador de portabilidad de .NET][]. Ejecute esta herramienta en el ensamblado compilado para determinar si son compatibles con .NET Framework, .NET Core y otros tiempos de ejecución .NET las API de .NET que se utiliza en el módulo. La herramienta sugiere API alternativas si existen. En caso contrario, es posible que deba agregar [comprobaciones en tiempo de ejecución][] y restringir las funciones no disponibles en los tiempos de ejecución específica.

## <a name="creating-a-new-module"></a>Crear un nuevo módulo

Si crea un nuevo módulo, la recomendación es usar el [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Instalar la plantilla de módulo de PowerShell estándar

Una vez que la CLI de .NET está instalada, instale una biblioteca de plantillas para generar un módulo de PowerShell simple.
El módulo será compatible con Windows PowerShell, PowerShell Core, Windows, Linux y macOS.

El ejemplo siguiente muestra cómo instalar la plantilla:

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

### <a name="creating-a-new-module-project"></a>Crear un nuevo proyecto de módulo

Después de instala la plantilla, puede crear un nuevo proyecto de módulo de PowerShell con esa plantilla. En este ejemplo, el módulo de ejemplo se denomina 'myModule'.

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

### <a name="building-the-module"></a>Compilación del módulo

Use los comandos de CLI de .NET estándar para compilar el proyecto.

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

### <a name="testing-the-module"></a>Probar el módulo

Después de compilar el módulo, puede importar y ejecutar el cmdlet de ejemplo.

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

Las secciones siguientes describen en detalle algunas de las tecnologías usadas por esta plantilla.

## <a name="net-standard-library"></a>Biblioteca estándar de .NET

[.NET standard][] es una especificación formal de las API de .NET que están disponibles en todas las implementaciones de. NET. Administrar código destinado a .NET Standard funciona con las versiones de .NET Framework y .NET Core que son compatibles con esa versión de .NET Standard.

> [!NOTE]
> Aunque puede existir una API en .NET Standard, la implementación de la API de .NET Core puede producir un `PlatformNotSupportedException` en tiempo de ejecución, por lo que para comprobar la compatibilidad con Windows PowerShell y PowerShell Core, el procedimiento recomendado es ejecutar pruebas para el módulo en ambos entornos.
> También debe ejecutar las pruebas en Linux y macOS si el módulo está pensado para ser multiplataforma.

.NET Standard como destino ayuda a garantizar que, a medida que evoluciona el módulo, las API incompatibles no accidentalmente obtener introducidas en el módulo. Se detectan incompatibilidades en tiempo de compilación en lugar de en tiempo de ejecución.

Sin embargo, no es necesario para el destino .NET Standard para un módulo para trabajar con Windows PowerShell y PowerShell Core, siempre que use las API compatibles. El lenguaje intermedio (IL) es compatible entre los dos tiempos de ejecución. Puede tener como destino .NET Framework 4.6.1, que es compatible con .NET Standard 2.0. Si no usa las API fuera de .NET Standard 2.0, a continuación, el módulo funciona con PowerShell Core 6 sin volver a compilar.

## <a name="powershell-standard-library"></a>Biblioteca estándar de PowerShell

El [Estándar de PowerShell][] biblioteca es una especificación formal de APIs de PowerShell disponibles en todas las versiones de PowerShell mayores o iguales que la versión de dicho estándar.

Por ejemplo, [Estándar de PowerShell 5.1][] es compatible con Windows PowerShell 5.1 y PowerShell Core 6.0 o posterior.

Se recomienda que compilar el módulo mediante la biblioteca estándar de PowerShell. La biblioteca garantiza que las API están disponibles e implementada en Windows PowerShell y PowerShell Core 6.
Estándar de PowerShell está diseñado para que siempre sea compatible con reenvíos. Un módulo compilado con PowerShell 5.1 de biblioteca estándar siempre será compatible con versiones futuras de PowerShell.

## <a name="module-manifest"></a>Manifiesto de módulo

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Que indica la compatibilidad con Windows PowerShell y PowerShell Core

Después de comprobar que el módulo funciona con Windows PowerShell y PowerShell Core, el manifiesto del módulo debe indicar explícitamente compatibilidad mediante el uso de la [CompatiblePSEditions][] propiedad. Un valor de `Desktop` significa que el módulo es compatible con Windows PowerShell, mientras que un valor de `Core` significa que el módulo es compatible con PowerShell Core. Las incluidas `Desktop` y `Core` significa que el módulo es compatible con Windows PowerShell y PowerShell Core.

> [!NOTE]
> `Core` no significa automáticamente que el módulo es compatible con Windows, Linux y macOS.
> El **CompatiblePSEditions** propiedad se introdujo en PowerShell v5. Manifiestos de módulo que usan el **CompatiblePSEditions** propiedad no se pudo cargar en las versiones anteriores de PowerShell v5.

### <a name="indicating-os-compatibility"></a>Que indica la compatibilidad de SO

En primer lugar, valide que el módulo funciona en Linux y macOS. A continuación, indicar la compatibilidad con esos sistemas operativos en el manifiesto del módulo. Esto facilita a los usuarios a encontrar el módulo para su sistema operativo cuando se publican en el [Galería de PowerShell][].

En el manifiesto del módulo, el `PrivateData` propiedad tiene un `PSData` subpropiedades. El elemento opcional `Tags` propiedad de `PSData` toma una matriz de valores que se muestran en la Galería de PowerShell. La Galería de PowerShell admite los siguientes valores de compatibilidad:

| Etiqueta               | Descripción                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatible con PowerShell Core 6          |
| PSEdition_Desktop | Compatible con Windows PowerShell         |
| Windows           | Compatible con Windows                    |
| Linux             | Compatible con Linux (ninguna distribución específica) |
| macOS             | Compatible con macOS                      |

Ejemplo:

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
[comprobaciones en tiempo de ejecución]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Estándar de PowerShell]: https://github.com/PowerShell/PowerShellStandard
[Estándar de PowerShell 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galería de PowerShell]: https://www.powershellgallery.com
[Analizador de portabilidad de .NET]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
