# Módulos con las ediciones compatibles de PowerShell
A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

## La edición de PowerShell que se está ejecutando se muestra en la propiedad PSEdition de $PSVersionTable.
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## Los autores de módulos pueden declarar sus módulos para hacerlos compatibles con una o varias ediciones de PowerShell mediante la clave de manifiesto del módulo CompatiblePSEditions. Esta clave solo se admite en PowerShell 5.1 o versiones posteriores.
*NOTA* Una vez que se especifica un manifiesto de módulo con la clave CompatiblePSEditions, no se puede importar en versiones anteriores de PowerShell.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$moduleInfo = Test-ModuleManifest -Path \TestModuleWithEdition.psd1
$moduleInfo.CompatiblePSEditions
Desktop
Core

$moduleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```
Al obtener una lista de los módulos disponibles, puede filtrarla según la edición de PowerShell.
```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

## Los autores de módulos pueden publicar un único módulo destinado a una de las ediciones de PowerShell o a ambas (Core o Desktop) 

Un único módulo puede trabajar tanto en la edición Desktop como Core; en este módulo, el autor tiene que agregar la lógica necesaria en RootModule o en el manifiesto del módulo mediante la variable $PSEdition.
Los módulos pueden tener dos conjuntos de archivos DLL que se dirijan a CoreCLR y a FullCLR.
A continuación, se indican un par de formas de empaquetar un módulo con la lógica correspondiente para cargar los archivos DLL adecuados.

### Opción 1: empaquetar un módulo para dirigirlo a varias versiones y varias ediciones de PowerShell

#### Contenido de la carpeta del módulo

 Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll Microsoft.Windows.PowerShell.ScriptAnalyzer.dll PSScriptAnalyzer.psd1 PSScriptAnalyzer.psm1 ScriptAnalyzer.format.ps1xml ScriptAnalyzer.types.ps1xml coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll en-US\about_PSScriptAnalyzer.help.txt en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll Settings\CmdletDesign.psd1 Settings\DSC.psd1 Settings\ScriptFunctions.psd1 Settings\ScriptingStyle.psd1 Settings\ScriptSecurity.psd1

#### Contenido del archivo PSScriptAnalyzer.psd1

```powershell
@{
 
# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### Contenido del archivo PSScriptAnalyzer.psm1
A continuación, la lógica carga los ensamblados necesarios en función de la edición o la versión actual.

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }    
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
} 

```

### Opción 2: usar la variable $PSEdition en el archivo. PSD1 para cargar los archivos DLL adecuados y los módulos anidados o necesarios

En PS 5.1 y versiones posteriores, se permite usar la variable global $PSEdition en el archivo de manifiesto de módulo.
Mediante esta variable el autor del módulo puede especificar los valores condicionales en el archivo de manifiesto de módulo. Se puede hacer referencia a la variable $PSEdition en modo de lenguaje restringido o en una sección de datos. 

*NOTA* Una vez que se especifica un manifiesto de módulo con la clave CompatiblePSEditions (o cuando usa la variable $PSEdition), no se puede importar en versiones anteriores de PowerShell.


#### Ejemplo de un archivo de manifiesto de módulo con la clave CompatiblePSEditions

```powershell
@{ 
# - - -
 
# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}
 
# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'
 
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}
 
# -- - -
}
```

#### Contenido del módulo

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
d-----         7/5/2016   1:37 PM                clr                                                                                 
d-----         7/5/2016   1:36 PM                coreclr                                                                             
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1                                                             
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl                                                                      
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl                                                                      
```

## Los usuarios de la Galería de PowerShell pueden encontrar la lista de módulos admitidos de edición específica de PowerShell mediante las etiquetas PSEdition_Desktop y PSEditon_Core.
Se considera que los módulos que no tienen las etiquetas PSEdition_Desktop o PSEditon_Core funcionan correctamente en las ediciones de PowerShell Desktop.

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEditon_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEditon_Core

```


## Más detalles
### [Scripts with PSEditions (Scripts con ediciones de PowerShell)](../script/scriptwithpseditionsupport.md)
### [PSEditions support on PowerShellGallery (Compatibilidad con las ediciones de PowerShell en la Galería de PowerShell)](../../psgallery/psgallery_pseditions.md)


<!--HONumber=Aug16_HO5-->


