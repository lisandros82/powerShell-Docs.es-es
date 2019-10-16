---
title: Cómo escribir el manifiesto de un módulo de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367104"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Cómo escribir un manifiesto de módulo de PowerShell

Una vez que haya escrito el módulo de Windows PowerShell, puede agregar opcionalmente un manifiesto de módulo. Un manifiesto de módulo es un archivo de script de PowerShell que puede usar para incluir información sobre el módulo. Por ejemplo, puede describir el autor, especificar archivos en el módulo (como módulos anidados), ejecutar scripts para personalizar el entorno del usuario, cargar archivos de formato y tipo, definir los requisitos del sistema y limitar los miembros que exporta el módulo.

## <a name="creating-a-module-manifest"></a>Crear un manifiesto de módulo

Un *manifiesto de módulo* es un archivo de datos de Windows PowerShell (. psd1) que describe el contenido de un módulo y determina cómo se procesa un módulo. El propio archivo de manifiesto es un archivo de texto que contiene una tabla hash de claves y valores. Para vincular un archivo de manifiesto a un módulo, asígnele el mismo nombre que el módulo y colóquelo en la raíz del directorio del módulo.

En el caso de los módulos simples que contienen solo un único psm1 o un ensamblado binario, un manifiesto de módulo es opcional. Sin embargo, se recomienda que use un manifiesto de módulo siempre que sea posible, ya que resulta útil para ayudarle a organizar el código y mantener la información de control de versiones. Además, se necesita un manifiesto de módulo para exportar un ensamblado que está instalado en la caché global de ensamblados. También se necesita un manifiesto de módulo para los módulos que admiten la característica de ayuda actualizable. Es decir, la ayuda actualizable usa la clave **HelpInfoUri** en el manifiesto del módulo para buscar el archivo de información de ayuda (HelpInfo XML) que contiene la ubicación de los archivos de ayuda actualizados para el módulo. Para obtener más información acerca de la ayuda actualizable, consulte compatibilidad con la [ayuda actualizable](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Para crear y usar un manifiesto de módulo

1. Para crear un manifiesto de módulo, tiene varias opciones:

   1. Cree directamente la tabla hash con la información mínima necesaria y guárdela en un archivo. psd1 que tenga el mismo nombre que el módulo. Una vez hecho esto, puede abrir el archivo y agregar manualmente los valores adecuados.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. O bien, llame al cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) , con uno o varios de los valores predeterminados pasados como parámetros. (Sin embargo, tenga en cuenta que solo es necesario el nombre del archivo para generar un manifiesto). Esto creará un manifiesto de módulo con todos los valores de manifiesto que proporcionó explícitamente y con el resto que contiene el valor predeterminado adecuado.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Por último, también puede crear un archivo. psd1 vacío y copiar la plantilla en la parte inferior de este tema en el archivo y rellenar los valores correspondientes. El único requisito real en este caso sería asegurarse de que el archivo tenía el mismo nombre que el módulo.

2. Agregue al manifiesto cualquier elemento adicional que desee incluir en el archivo.

   Por lo general, esto probablemente se hará en cualquier editor de texto que prefiera, como el Bloc de notas. Sin embargo, técnicamente es un archivo de script que contiene código, por lo que puede que desee editarlo en un entorno de desarrollo o scripting real, como Visual Studio Code. De nuevo, tenga en cuenta que todos los elementos de un archivo de manifiesto son opcionales, salvo el número de ModuleVersion.

   Para obtener descripciones de las claves y los valores que puede tener en un manifiesto del módulo, vea los **elementos del manifiesto del módulo** a continuación. Para obtener más información, consulte las descripciones de los parámetros en el cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

3. Opcionalmente, puede optar por agregar código adicional al manifiesto del módulo para abordar cualquier escenario que no esté incluido en los elementos del manifiesto del módulo base.

   Debido a los problemas de seguridad, PowerShell solo ejecutará un pequeño subconjunto de las operaciones disponibles en un archivo de manifiesto del módulo. Por lo general, puede usar la instrucción **If** , los operadores aritméticos y de comparación, y los tipos de datos básicos de PowerShell.

4. Una vez que haya creado el manifiesto del módulo, puede probarlo (para confirmar que las rutas de acceso descritas en el manifiesto son correctas) con una llamada a [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Asegúrese de que el manifiesto del módulo se encuentra en el nivel superior del directorio que contiene el módulo.

   Al copiar el módulo en un sistema e importarlo, PowerShell usará el manifiesto del módulo para importar el módulo.

6. Opcionalmente, puede probar directamente el manifiesto del módulo con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) mediante el origen del manifiesto.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementos del manifiesto del módulo

En la tabla siguiente se describen los elementos que puede tener en un manifiesto del módulo.

|Elemento|Valor predeterminado|Descripción|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Tipo: String|' '|Módulo de script o archivo de módulo binario asociado a este manifiesto. Las versiones anteriores de PowerShell llamaron a este elemento ModuleToProcess.<br /><br /> Los posibles tipos para el módulo raíz pueden estar vacíos (lo que hará que se trata de un módulo de **manifiesto** ), el nombre de un módulo de script (. psm1, que lo convierte en un módulo de **script** ), o el nombre de un módulo binario (. exe o. dll, que lo convierte en un módulo **binario** ). Si se coloca el nombre de un manifiesto de módulo (. psd1) o un archivo de script (. PS1) en este elemento, se producirá un error.|
|ModuleVersion<br /><br /> Tipo: String|1.0|Número de versión de este módulo. La cadena debe ser capaz de convertir a [System. Version]. Es decir, ' #. #. #. #. # '. `Import-Module` cargará el primer módulo que encuentre en el **$psModulePath** que coincida con el nombre, y tendrá al menos un valor de ModuleVersion, como el parámetro `-MinimumVersion`. Para importar una versión específica, utilice en su lugar el parámetro @ no__t-0.<br /><br /> Ejemplo: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Tipo: String|GUID generado automáticamente|IDENTIFICADOR usado para identificar de forma única este módulo. Tenga en cuenta que actualmente no se puede importar un módulo por GUID.<br /><br /> Ejemplo: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Tipo: String|Ninguno|Autor de este módulo.<br /><br /> Ejemplo: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Tipo: String|Unknown|Compañía o proveedor de este módulo.<br /><br /> Ejemplo: `CompanyName = 'Fabrikam'`|
|Propiedad intelectual<br /><br /> Tipo: String|(c) [currentYear] [autor]. Todos los derechos reservados.|Instrucción de copyright para este módulo.<br /><br /> Ejemplo: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Descripción<br /><br /> Tipo: String|' '|Descripción de la funcionalidad proporcionada por este módulo.<br /><br /> Ejemplo: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Tipo: String|' '|Versión mínima del motor de Windows PowerShell que requiere este módulo. Los valores válidos actuales son 1,0, 2,0, 3,0, 4,0 y 5,0.<br /><br /> Ejemplo: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Tipo: String|' '|Especifica el nombre del host de Windows PowerShell requerido por el módulo. Este nombre lo proporciona Windows PowerShell. Para buscar el nombre de un programa host, en el programa, escriba: `$host.name`.<br /><br /> Ejemplo: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Tipo: String|' '|Versión mínima del host de Windows PowerShell requerido por este módulo.<br /><br /> Ejemplo: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Tipo: String|' '|Versión mínima de Microsoft .NET Framework que requiere este módulo.<br /><br /> Ejemplo: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Tipo: String|' '|Versión mínima del Common Language Runtime (CLR) requerida por este módulo.<br /><br /> Ejemplo: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Tipo: String|' '|Arquitectura del procesador (ninguno, x86, AMD64) requerida por este módulo. Los valores válidos son x86, AMD64, IA64 y None (desconocido o no especificado).<br /><br /> Ejemplo: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Tipo: [String []]|@()|Módulos que se deben importar en el entorno global antes de importar este módulo. Esto cargará los módulos que se enumeran a menos que ya se hayan cargado. (por ejemplo, es posible que un módulo diferente ya haya cargado algunos módulos). También es posible especificar una versión específica para cargar mediante `RequiredVersion` en lugar de `ModuleVersion`. Al usar `ModuleVersion`, cargará la versión más reciente disponible con un mínimo de la versión especificada.<br /><br /> Ejemplo: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Ejemplo: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Tipo: [String []]|@()|Ensamblados que se deben cargar antes de importar este módulo.<br /><br /> Tenga en cuenta que, a diferencia de RequiredModules, PowerShell cargará el RequiredAssemblies si aún no se ha cargado.|
|ScriptsToProcess<br /><br /> Tipo: [String []]|@()|Archivos de script (. PS1) que se ejecutan en el estado de sesión del llamador cuando se importa el módulo. Podría ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Puede usar estos scripts para preparar un entorno del mismo modo que puede usar un script de inicio de sesión.<br /><br /> Estos scripts se ejecutan antes de que se cargue cualquiera de los módulos enumerados en el manifiesto.|
|TypesToProcess<br /><br /> Tipo: [String []]|@()|Archivos de tipo (. ps1xml) que se van a cargar al importar este módulo.|
|FormatsToProcess<br /><br /> Tipo: [String []]|@()|Archivos de formato (. ps1xml) que se van a cargar al importar este módulo.|
|NestedModules<br /><br /> Tipo: [String []]|@()|Módulos que se van a importar como módulos anidados del módulo especificado en RootModule/ModuleToProcess.<br /><br /> Agregar un nombre de módulo a este elemento es similar a llamar a `Import-Module` desde el código de ensamblado o script. La principal diferencia es que es más fácil ver lo que está cargando aquí en el archivo de manifiesto. Además, si un módulo no se carga aquí, todavía no habrá cargado el módulo real.<br /><br /> Además de otros módulos, también puede cargar archivos de script (. PS1) aquí. Estos archivos se ejecutarán en el contexto del módulo raíz. (Esto equivale a crear un punto de origen del script en el módulo raíz).|
|FunctionsToExport<br /><br /> Tipo: [String []]|@()|Especifica las funciones que exporta el módulo (se permiten caracteres comodín, pero se desaconsejan) al estado de sesión del llamador. De forma predeterminada, no se exporta ninguna función. Puede usar esta clave para enumerar las funciones que exporta el módulo.<br /><br /> El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todas las funciones exportadas por un módulo anidado se exportarán al estado de sesión global, a menos que un módulo de la cadena restrinja la función mediante la clave FunctionsToExport.<br /><br /> Si el manifiesto también exporta alias para las funciones, esta clave puede quitar funciones cuyos alias se enumeran en la clave AliasesToExport, pero esta clave no puede Agregar alias de función a la lista.|
|CmdletsToExport<br /><br /> Tipo: [String []]|@()|Especifica los cmdlets que exporta el módulo (los caracteres comodín están permitidos pero no se recomiendan). De forma predeterminada, no se exporta ningún cmdlet. Puede usar esta clave para enumerar los cmdlets que exporta el módulo.<br /><br /> El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todos los cmdlets exportados por un módulo anidado se exportarán finalmente al estado de sesión global, a menos que un módulo de la cadena restrinja el cmdlet mediante la clave CmdletsToExport.<br /><br /> Si el manifiesto también exporta alias para los cmdlets, esta clave puede quitar los cmdlets cuyos alias se muestran en la clave AliasesToExport, pero esta clave no puede Agregar alias de cmdlet a la lista.|
|VariablesToExport<br /><br /> Tipo: String|'*'|Especifica las variables que exporta el módulo (se permiten caracteres comodín) al estado de sesión del llamador. De forma predeterminada, se exportan todas las variables. Puede usar esta clave para restringir las variables que exporta el módulo.<br /><br /> El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todas las variables que exporta un módulo anidado se exportarán al estado de sesión global, a menos que un módulo de la cadena restrinja la variable mediante la clave VariablesToExport.<br /><br /> Si el manifiesto también exporta alias para las variables, esta clave puede quitar variables cuyos alias se enumeran en la clave AliasesToExport, pero esta clave no puede Agregar alias de variables a la lista.|
|AliasesToExport<br /><br /> Tipo: [String []]|@()|Especifica los alias que exporta el módulo (se permiten caracteres comodín, pero se desaconsejan) en el estado de sesión del llamador. De forma predeterminada, no se exporta ningún alias. Puede usar esta clave para mostrar los alias que exporta el módulo.<br /><br /> El estado de sesión del autor de la llamada puede ser el estado de sesión global o, en el caso de los módulos anidados, el estado de sesión de otro módulo. Al encadenar módulos anidados, todos los alias exportados por un módulo anidado se exportarán finalmente al estado de sesión global, a menos que un módulo de la cadena restrinja el alias mediante la clave AliasesToExport.|
|ModuleList<br /><br /> Tipo: [String []]|@()|Especifica todos los módulos que se empaquetan con este módulo. Estos módulos se pueden escribir por nombre (una cadena separada por comas) o como una tabla hash con las claves ModuleName y GUID. La tabla hash también puede tener una clave ModuleVersion opcional. La clave ModuleList está diseñada para actuar como un inventario de módulo. Estos módulos no se procesan automáticamente.|
|FileList<br /><br /> Tipo: [String []]|@()|Lista de todos los archivos empaquetados con este módulo. Al igual que con ModuleList, FileList le ayudará como una lista de inventario y, de otro modo, no se procesa.|
|PrivateData<br /><br /> Tipo: [objeto]|@{...}|Especifica cualquier dato privado que deba pasarse al módulo raíz especificado por la clave RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Tipo: String|' '|URI de HelpInfo de este módulo.|
|DefaultCommandPrefix<br /><br /> Tipo: String|' '|Prefijo predeterminado para los comandos exportados desde este módulo. Invalide el prefijo predeterminado mediante `Import-Module`-prefix.|

## <a name="sample-module-manifest"></a>Manifiesto del módulo de ejemplo

En el siguiente manifiesto del módulo de ejemplo se muestran las claves y los valores predeterminados de un manifiesto de módulo. Este ejemplo se creó mediante el cmdlet `New-ModuleManifest` en Windows PowerShell 3,0. Al crear varios módulos, puede usar este cmdlet para crear una plantilla de manifiesto que se puede modificar para módulos diferentes.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
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

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
