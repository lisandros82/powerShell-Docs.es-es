---
title: Cómo escribir el manifiesto de un módulo de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 4aa6c020cf0e82a4ffcad6f6c7540688d3369aa6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72561304"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Cómo escribir un manifiesto de módulo de PowerShell

Una vez que haya escrito el módulo de PowerShell, puede Agregar un manifiesto de módulo opcional que incluya información sobre el módulo. Por ejemplo, puede describir el autor, especificar archivos en el módulo (como módulos anidados), ejecutar scripts para personalizar el entorno del usuario, cargar archivos de formato y tipo, definir los requisitos del sistema y limitar los miembros que exporta el módulo.

## <a name="creating-a-module-manifest"></a>Crear un manifiesto de módulo

Un **manifiesto de módulo** es un archivo de datos de PowerShell (`.psd1`) que describe el contenido de un módulo y determina cómo se procesa un módulo. El archivo de manifiesto es un archivo de texto que contiene una tabla hash de claves y valores. Para vincular un archivo de manifiesto a un módulo, asigne al manifiesto el mismo nombre que el módulo y almacene el manifiesto en el directorio raíz del módulo.

En el caso de los módulos simples que contienen solo un único `.psm1` o un ensamblado binario, un manifiesto de módulo es opcional. Sin embargo, se recomienda usar un manifiesto de módulo siempre que sea posible, ya que resulta útil para ayudarle a organizar el código y mantener la información de control de versiones. Además, se necesita un manifiesto de módulo para exportar un ensamblado que está instalado en la [caché global de ensamblados](/dotnet/framework/app-domains/gac). También se necesita un manifiesto de módulo para los módulos que admiten la característica de ayuda actualizable. La ayuda actualizable usa la clave **HelpInfoUri** en el manifiesto del módulo para buscar el archivo de información de ayuda (HelpInfo XML) que contiene la ubicación de los archivos de ayuda actualizados para el módulo. Para obtener más información acerca de la ayuda actualizable, consulte compatibilidad con la [ayuda actualizable](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Para crear y usar un manifiesto de módulo

1. El procedimiento recomendado para crear un manifiesto de módulo es usar el cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) . Puede usar parámetros para especificar uno o más valores y claves predeterminados del manifiesto. El único requisito es asignar un nombre al archivo. `New-ModuleManifest` crea un manifiesto de módulo con los valores especificados e incluye las claves restantes y sus valores predeterminados. Si tiene que crear varios módulos, use `New-ModuleManifest` para crear una plantilla de manifiesto de módulo que se pueda modificar para los distintos módulos. Para obtener un ejemplo de un manifiesto de módulo predeterminado, vea el [manifiesto del módulo de ejemplo](#sample-module-manifest).

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   Una alternativa es crear manualmente la tabla hash del manifiesto del módulo con la información mínima necesaria, el **ModuleVersion**. Guarde el archivo con el mismo nombre que el módulo y use la extensión de archivo `.psd1`. A continuación, puede editar el archivo y agregar las claves y los valores adecuados.

1. Agregue los elementos adicionales que desee en el archivo de manifiesto.

   Para editar el archivo de manifiesto, use cualquier editor de texto que prefiera. Sin embargo, el archivo de manifiesto es un archivo de script que contiene código, por lo que puede que desee editarlo en un entorno de scripting o desarrollo, como Visual Studio Code. Todos los elementos de un archivo de manifiesto son opcionales, salvo el número de **ModuleVersion** .

   Para obtener descripciones de las claves y los valores que se pueden incluir en un manifiesto de módulo, vea la tabla de [elementos del manifiesto del módulo](#module-manifest-elements) . Para obtener más información, vea las descripciones de los parámetros en el cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

1. Para abordar cualquier escenario que podría no estar incluido en los elementos del manifiesto del módulo base, tiene la opción de agregar código adicional al manifiesto del módulo.

   Por motivos de seguridad, PowerShell solo ejecuta un pequeño subconjunto de las operaciones disponibles en un archivo de manifiesto del módulo. Por lo general, puede usar la instrucción `if`, operadores aritméticos y de comparación, y los tipos de datos básicos de PowerShell.

1. Después de crear el manifiesto del módulo, puede probarlo para confirmar que las rutas de acceso descritas en el manifiesto son correctas. Para probar el manifiesto del módulo, use [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

1. Asegúrese de que el manifiesto del módulo se encuentra en el nivel superior del directorio que contiene el módulo.

   Al copiar el módulo en un sistema e importarlo, PowerShell usa el manifiesto del módulo para importar el módulo.

1. Opcionalmente, puede probar directamente el manifiesto del módulo con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) mediante el origen del manifiesto.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementos del manifiesto del módulo

En la tabla siguiente se describen los elementos que se pueden incluir en un manifiesto del módulo.

|Elemento|Valor predeterminado|Descripción|
|-------------|-------------|-----------------|
|**RootModule**<br /> Tipo: `String`|`<empty string>`|Módulo de script o archivo de módulo binario asociado a este manifiesto. Las versiones anteriores de PowerShell llamaron a este elemento **ModuleToProcess**.<br /> Los posibles tipos del módulo raíz pueden estar vacíos, lo que crea un módulo de **manifiesto** , el nombre de un módulo de script (`.psm1`) o el nombre de un módulo binario (`.exe` o `.dll`). Si se coloca el nombre de un manifiesto de módulo (`.psd1`) o un archivo de script (`.ps1`) en este elemento, se produce un error. <br /> Ejemplo: `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> Tipo: `Version`|`'0.0.1'`|Número de versión de este módulo. Si no se especifica un valor, `New-ModuleManifest` utiliza el valor predeterminado. La cadena debe ser capaz de convertir al tipo `Version` por ejemplo `#.#.#.#.#`. `Import-Module` carga el primer módulo que encuentra en el **$PSModulePath** que coincide con el nombre y tiene al menos un número de **ModuleVersion**, como parámetro **MinimumVersion** . Para importar una versión concreta, use el parámetro **RequiredVersion** del cmdlet `Import-Module`.<br /> Ejemplo: `ModuleVersion = '1.0'`|
|**GUID**<br /> Tipo: `GUID`|`'<GUID>'`|IDENTIFICADOR usado para identificar de forma única este módulo. Si no se especifica un valor, `New-ModuleManifest` genera automáticamente el valor. Actualmente no se puede importar un módulo por **GUID**. <br /> Ejemplo: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Autor**<br /> Tipo: `String`|`'<Current user>'`|Autor de este módulo. Si no se especifica un valor, `New-ModuleManifest` utiliza el usuario actual. <br /> Ejemplo: `Author = 'AuthorNameHere'`|
|**Compañía**<br /> Tipo: `String`|`'Unknown'`|Compañía o proveedor de este módulo. Si no se especifica un valor, `New-ModuleManifest` utiliza el valor predeterminado.<br /> Ejemplo: `CompanyName = 'Fabrikam'`|
|**Copyright**<br /> Tipo: `String`|`'(c) <Author>. All rights reserved.'`| Instrucción de copyright para este módulo. Si no se especifica un valor, `New-ModuleManifest` utiliza el valor predeterminado con el usuario actual como `<Author>`. Para especificar un autor, use el parámetro **Author** . <br /> Ejemplo: `Copyright = '2019 AuthorName. All rights reserved.'`|
|**Descripción**<br /> Tipo: `String`|`<empty string>`|Descripción de la funcionalidad proporcionada por este módulo.<br /> Ejemplo: `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> Tipo: `Version`|`<empty string>`|Versión mínima del motor de PowerShell que requiere este módulo. Los valores válidos son 1,0, 2,0, 3,0, 4,0, 5,0, 5,1, 6 y 7.<br /> Ejemplo: `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> Tipo: `String`|`<empty string>`|Nombre del host de PowerShell requerido por este módulo. Este nombre lo proporciona PowerShell. Para buscar el nombre de un programa host, en el programa, escriba: `$host.name`.<br /> Ejemplo: `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> Tipo: `Version`|`<empty string>`|Versión mínima del host de PowerShell que requiere este módulo.<br /> Ejemplo: `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> Tipo: `Version`|`<empty string>`|Versión mínima de Microsoft .NET Framework que requiere este módulo. Este requisito previo solo es válido para la edición de escritorio de PowerShell, como PowerShell 5,1.<br /> Ejemplo: `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> Tipo: `Version`|`<empty string>`|Versión mínima del Common Language Runtime (CLR) requerida por este módulo. Este requisito previo solo es válido para la edición de escritorio de PowerShell, como PowerShell 5,1.<br /> Ejemplo: `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> Tipo: `ProcessorArchitecture`|`<empty string>`|Arquitectura del procesador (ninguno, x86, AMD64) requerida por este módulo. Los valores válidos son x86, AMD64, ARM, IA64, MSIL y None (desconocido o no especificado).<br /> Ejemplo: `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> Tipo: `Object[]`|`@()`|Módulos que se deben importar en el entorno global antes de importar este módulo. Esto carga los módulos enumerados a menos que ya se hayan cargado. (por ejemplo, es posible que un módulo diferente ya haya cargado algunos módulos). Es posible especificar una versión específica para cargar mediante `RequiredVersion` en lugar de `ModuleVersion`. Cuando se usa `ModuleVersion`, cargará la versión más reciente disponible con un mínimo de la versión especificada. Puede combinar las cadenas y las tablas hash en el valor del parámetro.<br /> Ejemplo: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> Ejemplo: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> Tipo: `String[]`|`@()`|Ensamblados que se deben cargar antes de importar este módulo. Especifica los nombres de archivo de ensamblado (`.dll`) que requiere el módulo.<br /> PowerShell carga los ensamblados especificados antes de actualizar los tipos o formatos, importar los módulos anidados o importar el archivo de módulo que se especifica en el valor de la clave RootModule. Use este parámetro para enumerar todos los ensamblados que requiere el módulo.<br /> Ejemplo: `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> Tipo: `String[]`|`@()`|Archivos de script (`.ps1`) que se ejecutan en el estado de sesión del llamador cuando se importa el módulo. Podría ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Puede usar estos scripts para preparar un entorno del mismo modo que puede usar un script de inicio de sesión.<br /> Estos scripts se ejecutan antes de que se cargue cualquiera de los módulos enumerados en el manifiesto. <br /> Ejemplo: `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> Tipo: `String[]`|`@()`|Archivos de tipo (`.ps1xml`) que se van a cargar al importar este módulo. <br /> Ejemplo: `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> Tipo: `String[]`|`@()`|Archivos de formato (`.ps1xml`) que se van a cargar al importar este módulo. <br /> Ejemplo: `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> Tipo: `Object[]`|`@()`|Módulos que se van a importar como módulos anidados del módulo especificado en **RootModule** (alias:**ModuleToProcess**).<br /> Agregar un nombre de módulo a este elemento es similar a llamar a `Import-Module` desde el código de ensamblado o script. La principal diferencia con el uso de un archivo de manifiesto es que es más fácil ver lo que está cargando. Además, si se produce un error al cargar un módulo, aún no se ha cargado el módulo real.<br /> Además de otros módulos, también puede cargar archivos de script (`.ps1`) aquí. Estos archivos se ejecutarán en el contexto del módulo raíz. Esto es equivalente a crear un punto de origen del script en el módulo raíz. <br /> Ejemplo: `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> Tipo: `String[]`|`@()`|Especifica las funciones que se van a exportar desde este módulo, para obtener el mejor rendimiento, no use caracteres comodín y no elimine la entrada, use una matriz vacía si no hay funciones para exportar. De forma predeterminada, no se exporta ninguna función. Puede usar esta clave para enumerar las funciones que exporta el módulo.<br /> El módulo exporta las funciones al estado de sesión del llamador. El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todas las funciones exportadas por un módulo anidado se exportarán al estado de sesión global, a menos que un módulo de la cadena restrinja la función mediante la clave **FunctionsToExport** .<br /> Si el manifiesto exporta alias para las funciones, esta clave puede quitar funciones cuyos alias se enumeran en la clave **AliasesToExport** , pero esta clave no puede Agregar alias de función a la lista. <br /> Ejemplo: `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> Tipo: `String[]`|`@()`|Especifica los cmdlets que se exportarán desde este módulo, para obtener el mejor rendimiento, no use caracteres comodín y no elimine la entrada, use una matriz vacía si no hay cmdlets para exportar. De forma predeterminada, no se exporta ningún cmdlet. Puede usar esta clave para enumerar los cmdlets que exporta el módulo.<br /> El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todos los cmdlets exportados por un módulo anidado se exportarán al estado de sesión global, a menos que un módulo de la cadena restrinja el cmdlet mediante la clave **CmdletsToExport** .<br /> Si el manifiesto exporta alias para los cmdlets, esta clave puede quitar los cmdlets cuyos alias se muestran en la clave **AliasesToExport** , pero esta clave no puede Agregar alias de cmdlet a la lista. <br /> Ejemplo: `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> Tipo: `String[]`|`'*'`|Especifica las variables que el módulo exporta al estado de sesión del llamador. Se permite el uso de caracteres comodín. De forma predeterminada, se exportan todas las variables (`'*'`). Puede usar esta clave para restringir las variables que exporta el módulo.<br /> El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todas las variables que exporta un módulo anidado se exportarán al estado de sesión global, a menos que un módulo de la cadena restrinja la variable mediante la clave **VariablesToExport** .<br /> Si el manifiesto también exporta alias para las variables, esta clave puede quitar variables cuyos alias se enumeran en la clave **AliasesToExport** , pero esta clave no puede Agregar alias de variables a la lista. <br /> Ejemplo: `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> Tipo: `String[]`|`@()`|Especifica los alias que se exportarán desde este módulo, para obtener el mejor rendimiento, no use caracteres comodín y no elimine la entrada, use una matriz vacía si no hay ningún alias para exportar. De forma predeterminada, no se exporta ningún alias. Puede usar esta clave para mostrar los alias que exporta el módulo.<br /> El módulo exporta los alias al estado de sesión del llamador. El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todos los alias exportados por un módulo anidado se exportarán finalmente al estado de sesión global, a menos que un módulo de la cadena restrinja el alias mediante la clave **AliasesToExport** . <br /> Ejemplo: `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> Tipo: `String[]`|`@()`|Especifica los recursos de DSC que se exportarán desde este módulo. Se permiten los caracteres comodín. <br /> Ejemplo: `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> Tipo: `Object[]`|`@()`|Especifica todos los módulos que se empaquetan con este módulo. Estos módulos se pueden escribir por nombre, mediante una cadena separada por comas o como una tabla hash con las claves **ModuleName** y **GUID** . La tabla hash también puede tener una clave **ModuleVersion** opcional. La clave **ModuleList** está diseñada para actuar como un inventario de módulo. Estos módulos no se procesan automáticamente. <br /> Ejemplo: `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**Lista de archivos**<br /> Tipo: `String[]`|`@()`|Lista de todos los archivos empaquetados con este módulo. Al igual que con **ModuleList**, **FileList** es una lista de inventario y no se procesa de otra manera. <br /> Ejemplo: `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> Tipo: `Object`|`@{...}`|Especifica cualquier dato privado que deba pasarse al módulo raíz especificado por la clave **RootModule** (alias: **ModuleToProcess**). **PrivateData** es una tabla hash que consta de varios elementos **: Tags**, **LicenseUri**, **ProjectURI**, **IconUri**, **releasenotes**, **versión preliminar**, **RequireLicenseAcceptance**y **ExternalModuleDependencies**. |
|**Etiquetas** <br /> Tipo: `String[]` |`@()`| Las etiquetas ayudan a la detección de módulos en las galerías en línea. <br /> Ejemplo: `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> Tipo: `Uri` |`<empty string>`| Una dirección URL a la licencia de este módulo. <br /> Ejemplo: `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> Tipo: `Uri` |`<empty string>`| Una dirección URL para el sitio web principal de este proyecto. <br /> Ejemplo: `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> Tipo: `Uri` |`<empty string>`| Una dirección URL a un icono que representa este módulo. <br /> Ejemplo: `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**Leame**<br /> Tipo: `String` |`<empty string>`| Especifica las notas de la versión del módulo. <br /> Ejemplo: `ReleaseNotes = 'The release notes provide information about the module.`|
|**Versión preliminar**<br /> Tipo: `String` |`<empty string>`| Este parámetro se agregó en PowerShell 7. Cadena de **versión preliminar** que identifica el módulo como versión preliminar en las galerías en línea. <br /> Ejemplo: `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> Tipo: `Boolean`|`$true`| Este parámetro se agregó en PowerShell 7. Marca que indica si el módulo requiere la aceptación explícita del usuario para instalar, actualizar o guardar. <br /> Ejemplo: `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> Tipo: `String[]` |`@()`| Este parámetro se agregó en PowerShell 7. Lista de módulos externos de los que depende este módulo. <br /> Ejemplo: `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> Tipo: `String`|`<empty string>`|URI de HelpInfo de este módulo. <br /> Ejemplo: `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> Tipo: `String`|`<empty string>`|Prefijo predeterminado para los comandos exportados desde este módulo. Invalide el prefijo predeterminado mediante `Import-Module -Prefix`. <br /> Ejemplo: `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>Manifiesto del módulo de ejemplo

El siguiente manifiesto del módulo de ejemplo se creó con `New-ModuleManifest` en PowerShell 7 y contiene las claves y los valores predeterminados.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>Consulta también

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[Caché global de ensamblados](/dotnet/framework/app-domains/gac)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
