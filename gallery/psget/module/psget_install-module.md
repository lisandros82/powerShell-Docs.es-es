---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: c066f4b34a03206cc0f31e9d40144fd719d9e305
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="install-module"></a>Install-Module

Instala los módulos de PowerShell desde repositorios en línea en el equipo local.

## <a name="description"></a>Descripción

El cmdlet Install-Module descarga de una galería en línea uno o más módulos, los valida y los instala en el equipo local en el ámbito de instalación especificado.

El cmdlet Install-Module obtiene de una galería en línea uno o varios módulos que cumplen los criterios especificados, comprueba que los resultados de la búsqueda son módulos válidos y copia carpetas de módulo en la ubicación de instalación.

Cuando no se define ningún ámbito o cuando el valor del parámetro Scope es AllUsers, el módulo se instala en %systemdrive%:\Program Files\WindowsPowerShell\Modules. Cuando el valor de Scope es CurrentUser, el módulo se instala en $home\Documents\WindowsPowerShell\Modules.

Puede filtrar los resultados en función de una versión mínima y exacta de los módulos especificados.

- Compatibilidad de versiones en paralelo en Windows PowerShell 5.0 o más reciente
- Compatibilidad con la instalación de dependencias de módulo
- **Aviso de no confianza:** se requiere la aceptación del usuario para instalar los módulos desde un repositorio que no es de confianza.
- -Force vuelve a instalar el módulo instalado.
- RequiredVersion instala la versión especificada en SxS con las versiones existentes en PowerShell versión 5.0 o posterior.

### <a name="scope"></a>Ámbito
Especifica el ámbito de instalación del módulo. Los valores aceptables para este parámetro son AllUsers y CurrentUser.

El ámbito de instalación predeterminado es AllUsers.

El ámbito AllUsers permite instalar módulos en una ubicación accesible para todos los usuarios del equipo, es decir, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".

El ámbito CurrentUser permite instalar módulos solo en "$home\Documents\WindowsPowerShell\Modules", de modo que el módulo solo está disponible para el usuario actual.

## <a name="notes"></a>Notas

Este cmdlet se ejecuta en Windows PowerShell 3.0 o versiones posteriores de Windows PowerShell, en Windows 7 o Windows 2008 R2 y versiones posteriores de Windows.

Si no se puede importar un módulo instalado (es decir, si no tiene un archivo .psm1, .psd1 o .dll con el mismo nombre en la carpeta), se produce un error en la instalación a menos que se agregue el parámetro Force al comando.

Si una versión del módulo en el equipo coincide con el valor especificado para el parámetro Name y no se ha agregado el parámetro MinimumVersion o RequiredVersion, Install-Module continúa en modo silencioso sin instalar ese módulo. Si se especifican los parámetros MinimumVersion o RequiredVersion y el módulo existente no coincide con los valores de ese parámetro, se produce un error. En concreto, se produce un error si la versión del módulo instalado actualmente es menor que el valor del parámetro MinimumVersion o si no es igual al valor del parámetro RequiredVersion. Si la versión del módulo instalado es mayor que el valor del parámetro MinimumVersion o igual al valor del parámetro RequiredVersion, Install-Module continúa en modo silencioso sin instalar ese módulo.

Install-Module devuelve un error si no existe ningún módulo en la galería en línea que coincida con el nombre especificado.

Para instalar varios módulos, especifique una matriz de los nombres de módulo, separados por comas. No se puede agregar MinimumVersion o RequiredVersion si se especifican varios nombres de módulo.

De forma predeterminada, los módulos se instalan en la carpeta Archivos de programa, para evitar confusiones al instalar recursos de configuración de estado deseado de Windows PowerShell (DSC). Puede canalizar varios objetos PSGetItemInfo a Install-Module. Se trata de otra manera de especificar varios módulos para instalarlos en un solo comando.

Para evitar la ejecución de módulos que contienen código malintencionado, la instalación no importa automáticamente los módulos instalados. Como procedimiento de seguridad recomendado, evalúe el código del módulo antes de ejecutar un cmdlet o una función en un módulo por primera vez.


## <a name="cmdlet-syntax"></a>Sintaxis de cmdlet
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referencia de la ayuda en línea de cmdlet

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a>Comandos de ejemplo

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name 
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a>Cmdlet Install-Module en operaciones de canalización

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Compatibilidad de versiones en paralelo en PowerShell 5.0 o posterior

PowerShellGet incluye compatibilidad de versiones de módulos en paralelo (SxS) en los cmdlets Install-Module, Update-Module y Publish-Module que se ejecutan en Windows PowerShell 5.0 o versiones más recientes.

### <a name="install-module-examples"></a>Ejemplos de Install-Module

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a>Instalar un módulo con sus dependencias

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a>Escenarios de error

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```

